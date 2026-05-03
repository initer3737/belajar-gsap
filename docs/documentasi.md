***
#### gsap adalah greensock animation platform adalah platform berbasis javascript library yang digunakkan untuk membuat animasi dan telah digunakkan oleh hampir 11 juta website di dunia

***
### to: dari posisi yang ditentukan menuju ke x
```javascript
  gsap.to('.box1',{
        duration:2,
        x:300,
        opacity:0
    })

```
- single animation disebut juga tween contohnya dibawah ini satu kode disebut dengan tween
### from: dari posisi awal misal y :-240 menuju ke posisi ke posisi y:0 karena posisi to tidak diisi
- gsap from menganimasikan kondisi dari state akhir ke state saat ini ,awal dari y adalah -240px lalu berjalan ke 0 atau posisi saat ini
  
```javascript
  gsap.from(".box2",{
        duration:3,
        delay:1,
        y:-240
    })

```

### fromTo: dari posisi awal misal/from ke posisi to 
- gsap fromTo menganimasikan kondisi dari state akhir ke state saat ini ,awal dari y adalah -240px lalu berjalan ke 0 atau posisi saat ini
  
```javascript
const data={
    from:{
        duration:3,
        delay:1,
        y:-240
    },
   to:{
        duration:3,
        delay:1,
        y:0
    }
}
  gsap.fromTo(".box2",data.from,data.to)

```

### set: menentukan posisi element di dom 
- gsap set menentukan letak element di posisi mana  
- misal opacity diset 0 dan koordinat y ada di -200 saat animasi belum dijalankan
  
```javascript

  gsap.set(".box2",{
    opacity:0,
    y:-240px
  })

```

### lifecycle 
- gsap onComplete menentukan saat dimana animasi telah selesai dijalankan  
- gsap onUpdate menentukkan saat dimana animasi sedang berjalan
  
```javascript
    // Animasi GSAP
    const wrapper2=".wrapper-2 "
    const score = document.querySelector(wrapper2+' .score')
    gsap.to(wrapper2+' .box', { duration: 2, x:-122,autoAlpha:0, stagger:1, ease: "none" ,onComplete:function(){
        gsap.to(wrapper2+'.box',{ duration: 2, x:5,autoAlpha:1, stagger:1.5, ease: "none",delay:1,repeatDelay:0.5})
        score.textContent=" selesai"
    },onUpdate:function(){
        const percentage=this.progress()
        // score.textContent=Math.round(gsap.getProperty('.box','x'))
        score.textContent=percentage>=0.5?`percentage ${(percentage*100).toFixed(0)} time ${this.time().toFixed(1)}`:null
    }});
```

### timeline 
- mengurutkan animasi secara berantai kalau animasi sebelumnya seelesai maka eksekusi animasi berikutnya 
- angka seperti "-=0.5 itu menunggu sekitar -dari sama dengan 0.5 lalu animasi akan dieksekusi"
- "<"	Start Alignment	Mulai bersamaan dengan awal animasi sebelumnya.
- ">"	End Alignment	Mulai tepat saat animasi sebelumnya selesai (default).

```javascript
     // Animasi GSAP
    const wrapper3=".wrapper-3 "
    const tl=gsap.timeline()
        tl
        .to(wrapper3+" .box0",{x:-250,opacity:1})
        .to(wrapper3+" .box1",{x:-250,opacity:1},"-=0.5")
        .to(wrapper3+" .box2",{x:-250,opacity:1},"<=2.9")
        .to(wrapper3+" .box3",{x:-250,opacity:1},2.5)
```

```javascript
     // Animasi GSAP
    const wrapper3=".wrapper-3 "
    const tl=gsap.timeline()
       tl.addLabel("mulai")
        .to(".box", {x: 200})
        .addLabel("tengah")
        .to(".box", {y: 200})
  
tl.seek("tengah") // langsung lompat ke label "tengah"
```

```javascript

|---A---| 
    |---B---|   ← B mulai 0.5s sebelum A selesai = "-=0.5"
|---A---|
         |---B---|   ← B delay 1s setelah A selesai = "+=1"
|---A---|
         |---B---|   ← a barengan sama b = "<"
|---A---|
         |---B---|   ← a barengan sama b tapi tunggu a sekitar 1 detik  = "<1"

     // Animasi GSAP
    const tl = gsap.timeline({ paused: true }) // bikin dulu tapi jangan play
tl.to(".box", {x: 500})

// Nanti bisa:
tl.play()    // play
tl.pause()   // pause
tl.reverse() // mundur
tl.progress(0.5) // lompat ke 50%

tl.addLabel("masuk") // Membuat tanda/label bernama "masuk"
  .to(".box1", {x: 100}, "masuk")
  .to(".box2", {y: 100}, "masuk+=2.9") // Jalan 2.9 detik setelah label "masuk"
```

### gsap memecahkan permasalahan dari membuat keyframe/animation manual yang dilihat mustahil dilakukan menjadi mustahil

[read docs](https://gsap.com/resources/get-started//)
[kenapa belajar gsap](https://gsap.com/blog/why-gsap/)

#### gsap menganimasikan dom element menjadi mudah untuk dilakukan mencoba untuk membuatnya menggunakkan css keyframe manual akan sangat susah , dan inilah kenapa gsap : 
- gsap sudah menjadi standard industri
- google merekomendasikan gsap untuk animasi javascript
- hampir 11 juta website menggunakkan gsap 
  
  ### baiknya gunakkan

  - transform seperti x y dan opacity 
  - jangan gunakkan left top bottom right untuk mendapatkan animasi yang smooth
  - jangan menggunakkan filter maupun box-shadow karena resource intensive untuk browser me render animasinya test di low device jika bisa , gunakkan transform dan opacity