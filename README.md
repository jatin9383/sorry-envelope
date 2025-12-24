# sorry-envelope
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Sorry Baby ❤️</title>

<style>
body{
    margin:0;
    height:100vh;
    display:flex;
    justify-content:center;
    align-items:center;
    background:#fff0f5;
    overflow:hidden;
    font-family:'Segoe UI',sans-serif;
}

/* Envelope */
.envelope{
    width:280px;
    height:180px;
    position:relative;
    cursor:pointer;
}
.body{
    background:#ffb6c1;
    width:100%;
    height:100%;
    border-radius:12px;
    position:relative;
    overflow:hidden;
}

/* Flap */
.flap{
    position:absolute;
    top:0;
    left:0;
    width:0;
    height:0;
    border-left:140px solid transparent;
    border-right:140px solid transparent;
    border-top:90px solid #ff69b4;
    transform-origin:top;
    transition:0.8s;
}

/* Paper */
.paper{
    position:absolute;
    bottom:-160px;
    left:15px;
    width:250px;
    height:150px;
    background:white;
    border-radius:6px;
    padding:12px;
    text-align:center;
    box-shadow:0 8px 20px rgba(0,0,0,0.3);
    transform:scaleY(0.4);
    transition:1.4s ease;
}

/* Open */
.open .flap{
    transform:rotateX(180deg);
}
.open .paper{
    bottom:25px;
    transform:scaleY(1);
}

/* Button */
button{
    margin-top:10px;
    padding:10px 26px;
    background:red;
    color:white;
    border:none;
    border-radius:30px;
    font-size:15px;
    opacity:0;
    transition:1.5s;
    cursor:pointer;
}

/* Sorry rain */
.sorry{
    position:absolute;
    top:-30px;
    color:red;
    font-size:18px;
    animation:fall linear infinite;
}
@keyframes fall{
    to{transform:translateY(110vh);}
}

/* Image screen */
#imagePage{
    display:none;
    position:absolute;
    inset:0;
    background:black;
    justify-content:center;
    align-items:center;
}
#imagePage img{
    max-width:90%;
    border-radius:18px;
}
</style>
</head>

<body>

<div class="envelope" onclick="openEnv(this)">
    <div class="body">
        <div class="flap"></div>

        <div class="paper">
            <p>
            Sorry baby abb nhi kerunga<br>
            aise bura lagega<br>
            ye sab nahi sochunga<br>
            bata diya kerunga<br>
            please mujhe maaf kerdo<br>
            sorrryyy ❤️
            </p>
            <button id="nextBtn" onclick="showImage(event)">Next</button>
        </div>
    </div>
</div>

<div id="imagePage">
    <img src="photo.jpg">
</div>

<script>
function openEnv(env){
    env.classList.add("open");
    startSorry();

    setTimeout(()=>{
        document.getElementById("nextBtn").style.opacity="1";
    },1500);
}

function startSorry(){
    setInterval(()=>{
        let s=document.createElement("div");
        s.className="sorry";
        s.innerText="SORRY";
        s.style.left=Math.random()*100+"vw";
        s.style.animationDuration=2+Math.random()*3+"s";
        document.body.appendChild(s);
        setTimeout(()=>s.remove(),5000);
    },220);
}

function showImage(e){
    e.stopPropagation();
    document.getElementById("imagePage").style.display="flex";
    startSorry();
}
</script>

</body>
</html>
