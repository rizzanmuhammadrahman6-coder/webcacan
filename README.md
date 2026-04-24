<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<title>Untuk Cacan 💖</title>

<style>
body{
    margin:0;
    background:black;
    overflow:hidden;
    font-family: 'Segoe UI', sans-serif;
    color:white;
    text-align:center;
}

/* Bintang */
.star{
    position:absolute;
    width:2px;
    height:2px;
    background:white;
    animation: blink 2s infinite;
}

@keyframes blink{
    0%,100%{opacity:0}
    50%{opacity:1}
}

/* Text */
#text{
    position:absolute;
    top:40%;
    width:100%;
    font-size:24px;
    opacity:0;
    transition:1s;
}

/* Heart */
.heart{
    position:absolute;
    color:pink;
    font-size:20px;
    animation: fall linear infinite;
}

@keyframes fall{
    0%{transform:translateY(-10vh);}
    100%{transform:translateY(110vh);}
}

/* LOVE tengah */
#love{
    position:absolute;
    top:50%;
    left:50%;
    transform:translate(-50%,-50%) scale(0);
    font-size:60px;
    color:pink;
    transition:1s;
}
</style>
</head>

<body>

<audio autoplay loop>
    <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
</audio>

<div id="text"></div>
<div id="love">❤️</div>

<script>

// ⭐ bintang
for(let i=0;i<100;i++){
    let s=document.createElement("div");
    s.className="star";
    s.style.top=Math.random()*100+"vh";
    s.style.left=Math.random()*100+"vw";
    document.body.appendChild(s);
}

// 💞 hujan hati
setInterval(()=>{
    let h=document.createElement("div");
    h.className="heart";
    h.innerHTML="❤";
    h.style.left=Math.random()*100+"vw";
    h.style.animationDuration=(3+Math.random()*2)+"s";
    document.body.appendChild(h);

    setTimeout(()=>h.remove(),5000);
},200);

// 💌 teks romantis
let teks=[
"di saat cacan bobo aku lagi buat ini...",
"aku kangen banget sama cacan 💖",
"aku sayang banget sama cacan",
"",
"pagi, can ☀️",
"semoga hari kamu penuh kebahagiaan",
"aku ga selalu ada...",
"tapi aku selalu ada buat kamu ❤️",
"",
"aku sayang cacan selamanya",
"dan aku cinta cacan selamanya 💞"
];

let i=0;
let el=document.getElementById("text");

function tampil(){
    if(i<teks.length){
        el.style.opacity=0;
        setTimeout(()=>{
            el.innerHTML=teks[i];
            el.style.opacity=1;
        },500);
        i++;
        setTimeout(tampil,3000);
    }else{
        document.getElementById("love").style.transform="translate(-50%,-50%) scale(1.5)";
    }
}

setTimeout(tampil,2000);

</script>

</body>
</html>
