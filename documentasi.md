***
#### gsap adalah greensock animation platform adalah platform berbasis javascript library yang digunakkan untuk membuat animasi dan telah digunakkan oleh hampir 11 juta website di dunia

***
### dari posisi yang ditentukan menuju ke x
```javascript
  gsap.to('.box1',{
        duration:2,
        x:300,
        opacity:0
    })

```
- single animation disebut juga tween contohnya dibawah ini satu kode disebut dengan tween

```javascript
  gsap.from(".box2",{
        duration:3,****
        delay:1,
        y:-240
    })

```

### gsap memecahkan permasalahan dari membuat keyframe/animation manual yang dilihat mustahil dilakukan menjadi mustahil

[kenapa belajar gsap](https://gsap.com/blog/why-gsap/)

#### gsap menganimasikan dom element menjadi mudah untuk dilakukan mencoba untuk membuatnya menggunakkan css keyframe manual akan sangat susah , dan inilah kenapa gsap : 
- gsap sudah menjadi standard industri
- google merekomendasikan gsap untuk animasi javascript
- hampir 11 juta website menggunakkan gsap