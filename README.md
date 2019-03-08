# QFrameLessWindow

### It is simple example of borderless window in Qt.

## Using

1) Clone the repo
2) Add to your .pro file:
```
HEADERS += /path_to/widget.hpp
SOURCES += /path_to/widget.cpp
```
3) Include `widget.hpp` and create example of window:
```c++
#include "/path_to/widget.hpp"

qt_extended::widget wnd;
wnd.show();
```

## Your own widget

You can create your own class using public inheritance:

```c++
class your_widget : public qt_extended::widget {
  ...
};
```

All your widgets should be add to `qt_extended::widget::main_layout` (Vertical allignment):

```c++
QPushButton *button = new QPushButton;
main_layout->addWidget(button);
```

You can add any widgets in title_bar (All widgets should be add to `qt_extended::title_bar::main_layout` (Horizontal allignment)):

```c++
get_title_bar()->main_layout->addWidget(button);
```

You can get access to default ui in title_bar (header, 3 tool buttons and common layout):

```c++
get_title_bar()->get_ui().icon; // QLabel
get_title_bar()->get_ui().title; // QLabel
get_title_bar()->get_ui().close_button; // QPushButton
get_title_bar()->get_ui().maximize_button; // QPushButton
get_title_bar()->get_ui().minimize_button; // QPushButton
get_title_bar()->get_ui().layout; // QHBoxLayout
```

For default, icon is hide. You can show icon with this code:

```c++
get_title_bar()->get_ui().icon->show();
```

## QSS

You can customize your widget using qss:

```css
qt_extended--widget {
  // widget styles
}

.title_bar {
  // title_bar styles
}

.icon {
  border-image: url(":/appIcon.ico") 0 0 0 0 stretch;
}

.title {
  // title in title_bar styles
}

.close_button {
  // close button styles
}

.minimize_button {
  // minimize button styles
}

.maximize_button {
  // maximize button styles
}

*[title_button=true] {
  // close, minimize, maximize buttons styles
}
```

Check more about qss: https://doc.qt.io/qt-5/stylesheet-reference.html