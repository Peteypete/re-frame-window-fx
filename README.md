# re-frame-window-fx

[![Build Status](https://travis-ci.org/district0x/re-frame-window-fx.svg?branch=master)](https://travis-ci.org/district0x/re-frame-window-fx)

[re-frame](https://github.com/Day8/re-frame) effect handlers related to browser window.

## Installation
Add `[district0x/re-frame-window-fx "1.0.0"]` into your project.clj    
Include `[district0x.re-frame.window-fx]` in your CLJS file

## Usage
#### `:window/on-resize`
Fires `:dispatch` when browser window is resized. Can set `:debounce-ms` for debouncing event, to prevent too frequent firings.  
Default `:debounce-ms` is 166ms.  
Dispatched event receives `[js/window.innerWidth js/window.innerHeight]` as a last arg. 
```clojure
(reg-event-fx
  ::my-event
  (fn []
    {:window/on-resize {:dispatch [::window-resized]
                        :debounce-ms 200}}))
```
#### `:window/on-focus`
Fires `:dispatch` when tab/window receives focus
```clojure
(reg-event-fx
  ::my-event
  (fn []
    {:window/on-focus {:dispatch [::window-focused]}}))
```
#### `:window/on-blur`
Fires `:dispatch` when tab/window was blurred
```clojure
(reg-event-fx
  ::my-event
  (fn []
    {:window/on-blur {:dispatch [::window-blurred]}}))
```
#### `:window/on-hashchange`
Fires `:dispatch` when location hash was changed
```clojure
(reg-event-fx
  ::my-event
  (fn []
    {:window/on-hashchange {:dispatch [::window-hashchanged]}}))
```
#### `:window/scroll-to`
Scroll window into x y coordinates
```clojure
(reg-event-fx
  ::my-event
  (fn []
    {:window/scroll-to [100 200]}))
```
## Development
```bash
lein deps

# To run tests and rerun on changes
lein doo chrome tests
```
