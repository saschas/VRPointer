# VRPointer

### How to use it
Load the **VRPointer** script before you use it:
`<script type="text/javascript" src="<--YOUR-PATH-->/VRPointer.js"></script>`

#### Initialize VR Pointer
Initialize the VR Pointer with the threejs `camera` and `scene`. All other params are optional.

```js
var vr_pointer = new VRPointer({
    //not optional
    camera : camera,
    scene : scene,
    
    //optional
    strokeWidth : 2,                  
    midPoint : new THREE.Vector2(0,0),
    distanceFromCamera : 50,          
    color : '#ffffff',                
    opacity : 0.75,                   
    size : 1,                         
    duration : 100,                   

    // active element options
    activeElements : [{                 
      elements : screenObjects,         //array
      duration : 50,                    //individual Duration
      hover : function (o){             //mouseover
       //o.element
       //o.point
       //o.distance
      },
      out : function(o){                //mouseout
        //o.element
        //o.point
        //o.distance
      },
      click : function (o){             //click
        //o.element
        //o.point
        //o.distance
      }
    }]
  });

// render loop
function render() { 
  requestAnimationFrame( render );

  //update on frame
  vr_pointer.update();
}

render();

```


| parameter          | optional      | type      | default  | description  |
| :-------------     |:-------------:|:-------------| :--------| :------------|
| camera             | no            | object              | -        | Camera |
| scene              | no            | object            | -        | scene the pointer is append to   |
| midpoint           | yes           | vec2           | new THREE.Vector2(0,0) | Set the location for the Pointer. Default is in the center of the window. |
| distanceFromCamera | yes           | number           | 50       | Pointer distance relative to camera |
| color              | yes           | hex Color           | #ffffff  | Color of the Pointer |
| opacity            | yes           | number           | 0.75     | Circle fill opacity while hovering  |
| size               | yes           | number           | 1        | Size of Pointer  |
| duration           | yes           | number           | 100      | How long you have to look at the element before the click function executes?  |
| activeElements     | yes           | array           | -        | Define active Elements. See table below for more info  |


###Options for activeElements

| parameter          | optional      | type      | default  | description  |
| -------------      |:-------------:|:----------| :--------| :------------|
| elements           | no            | array     | -        | Which elements should be active |
| duration           | yes           | number    | Default is the VRPointer duration.  | Individual Lookat Duration for elements before click is fired.|
| hover              | yes           | function  | -  | Fires when pointer looks at an active element. Parameter is an object(element,point,distance)  |
| out                | yes           | function  | -  | Fires when pointer leave an active element. Parameter is an object(element,point,distance)  |
| click              | yes           | function  | -  | Fires when pointer looks at an active element for certain duration. Parameter is an object(element,point,distance)|
