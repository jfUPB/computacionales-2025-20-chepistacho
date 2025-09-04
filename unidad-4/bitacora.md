# Evidencias para la unidad 4

## Código

Código para ofApp.h:

``` cpp
#pragma once
#include "ofMain.h"

// Nodo de la cola
struct Node {
	float x, y;
	float radius;
	ofColor color;
	float opacity;
	Node * next;

	Node(float _x, float _y, float _radius, ofColor _color, float _opacity)
		: x(_x)
		, y(_y)
		, radius(_radius)
		, color(_color)
		, opacity(_opacity)
		, next(nullptr) {
	}
};

// Implementación manual de una cola (FIFO)
class BrushQueue {
public:
	Node * front;
	Node * rear;
	int size;
	int maxSize;

	BrushQueue(int _maxSize);
	~BrushQueue();

	void enqueue(float x, float y, float radius, ofColor color, float opacity);
	void dequeue();
	void clear();
	bool isEmpty(int size);
};

// Constructor
BrushQueue::BrushQueue(int _maxSize)
	: front(nullptr)
	, rear(nullptr)
	, size(0)
	, maxSize(_maxSize) { }

// Destructor
BrushQueue::~BrushQueue() {
	clear();
}

// Implementa aquí `enqueue()`
void BrushQueue::enqueue(float x, float y, float radius, ofColor color, float opacity) {
	Node * n = new Node(x, y, radius, color, opacity);

	if (rear == nullptr) {
		front = rear = n;
	} else {
		rear->next = n;
		rear = n;
	}
	size++;

	while (size > maxSize) {
		dequeue();
	}

	int i = 0;
	for (Node * cur = front; cur != nullptr; cur = cur->next, ++i) {
		float a = ofMap(i, 0, std::max(1, size - 1), 40.0f, 255.0f, true);
		cur->opacity = a;
	}
}

// Implementa aquí `dequeue()`
void BrushQueue::dequeue() {
	if (front == nullptr) return;
	Node * old = front;
	front = front->next;
	if (front == nullptr) {
		rear = nullptr;
	}
	delete old;
	size = std::max(0, size - 1);
}

// Implementa aquí `clear()`
void BrushQueue::clear() {
	while (front != nullptr) {
		Node * tmp = front;
		front = front->next;
		delete tmp;
	}
	rear = nullptr;
	size = 0;
}

// Implementa aquí `isEmpty()`
bool BrushQueue::isEmpty(int size) {
	if (BrushQueue::size = 0) {
		return true;
	} else {
		return false;
	}
}

class ofApp : public ofBaseApp {
public:
	BrushQueue strokes; // Cola de trazos
	float backgroundHue = 0;

	ofApp()
		: strokes(50) { } // Tamaño máximo de la cola

	void setup();
	void update();
	void draw();
	void keyPressed(int key);
};


```

Código para ofApp.cpp:

``` cpp
#include "ofApp.h"

//--------------------------------------------------------------
void ofApp::setup() {
	ofBackground(0);
	ofSetCircleResolution(48);
	ofEnableAlphaBlending();
}

//--------------------------------------------------------------
void ofApp::update() {
	backgroundHue += 0.2f;
	if (backgroundHue > 255.0f) backgroundHue = 0.0f;

	if (ofGetMousePressed(OF_MOUSE_BUTTON_LEFT)) {
		float x = (float)ofGetMouseX();
		float y = (float)ofGetMouseY();

		float radius = ofRandom(8.0f, 14.0f);
		float hue = ofRandom(0, 255);
		ofColor c = ofColor::fromHsb(hue, 200, 255);

		strokes.enqueue(x, y, radius, c, 255.0f);
	}
}

//--------------------------------------------------------------
void ofApp::draw() {
	ofColor color1, color2;
	color1.setHsb(backgroundHue, 150, 240);
	color2.setHsb(fmod(backgroundHue + 128.0f, 255.0f), 150, 240);
	ofBackgroundGradient(color1, color2, OF_GRADIENT_LINEAR);

	for (Node * cur = strokes.front; cur != nullptr; cur = cur->next) {
		ofSetColor(cur->color.r, cur->color.g, cur->color.b, cur->opacity);
		ofDrawCircle(cur->x, cur->y, cur->radius);
	}
}

//--------------------------------------------------------------
void ofApp::keyPressed(int key) {
	if (key == 'c') {
		strokes.clear();
	}
	if (key == 'a') {
		strokes.maxSize = (strokes.maxSize == 50) ? 100 : 50;
		while (strokes.size > strokes.maxSize) {
			strokes.dequeue();
		}
		int i = 0;
		for (Node * cur = strokes.front; cur != nullptr; cur = cur->next, ++i) {
			float a = ofMap(i, 0, std::max(1, strokes.size - 1), 40.0f, 255.0f, true);
			cur->opacity = a;
		}
	} else if (key == 's') {
		string fname = "brush_" + ofGetTimestampString("%Y%m%d_%H%M%S") + ".png";
		ofSaveScreen(fname);
		ofLogNotice() << "Guardado: " << fname;
	}
}


```

Código para main.cpp:
``` cpp
#include "ofMain.h"
#include "ofApp.h"

//========================================================================
int main( ){

	//Use ofGLFWWindowSettings for more options like multi-monitor fullscreen
	ofGLWindowSettings settings;
	settings.setSize(1024, 768);
	settings.windowMode = OF_WINDOW; //can also be OF_FULLSCREEN

	auto window = ofCreateWindow(settings);

	ofRunApp(window, std::make_shared<ofApp>());
	ofRunMainLoop();

}


```

## Demostración:

[Aquí está el video demostrativo de mi aplicación](https://youtu.be/8RmsqeQ7t5M)


