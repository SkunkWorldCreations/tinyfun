
<style>
* { box-sizing: border-box; margin: 0; padding: 0; }
body { font-family: var(--font-sans); }
#hub { padding: 2rem 1rem; }
h1.site-title { font-size: 28px; font-weight: 500; color: var(--color-text-primary); text-align: center; margin-bottom: 4px; }
p.site-sub { text-align: center; font-size: 15px; color: var(--color-text-secondary); margin-bottom: 2rem; }
.game-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(180px, 1fr)); gap: 12px; margin-bottom: 2rem; }
.game-card { background: var(--color-background-primary); border: 0.5px solid var(--color-border-tertiary); border-radius: var(--border-radius-lg); padding: 1.25rem 1rem; cursor: pointer; transition: border-color 0.15s, transform 0.1s; text-align: center; }
.game-card:hover { border-color: var(--color-border-primary); transform: translateY(-2px); }
.game-card .icon { font-size: 32px; margin-bottom: 8px; }
.game-card .name { font-size: 14px; font-weight: 500; color: var(--color-text-primary); margin-bottom: 4px; }
.game-card .desc { font-size: 12px; color: var(--color-text-secondary); line-height: 1.4; }
#game-container { display: none; background: var(--color-background-primary); border: 0.5px solid var(--color-border-tertiary); border-radius: var(--border-radius-lg); padding: 1.5rem; }
.back-btn { background: none; border: 0.5px solid var(--color-border-secondary); border-radius: var(--border-radius-md); padding: 6px 14px; font-size: 13px; color: var(--color-text-secondary); cursor: pointer; margin-bottom: 1.25rem; display: inline-flex; align-items: center; gap: 6px; }
.back-btn:hover { background: var(--color-background-secondary); }
.game-title { font-size: 20px; font-weight: 500; color: var(--color-text-primary); margin-bottom: 4px; }
.game-subtitle { font-size: 14px; color: var(--color-text-secondary); margin-bottom: 1.5rem; }
.big-num { font-size: 52px; font-weight: 500; color: var(--color-text-primary); line-height: 1; }
.big-label { font-size: 13px; color: var(--color-text-secondary); margin-top: 4px; }
.game-btn { display: inline-block; border: 0.5px solid var(--color-border-secondary); border-radius: var(--border-radius-md); padding: 10px 24px; font-size: 15px; cursor: pointer; background: none; color: var(--color-text-primary); margin-top: 1rem; transition: background 0.1s; }
.game-btn:hover { background: var(--color-background-secondary); }
.game-btn:active { transform: scale(0.98); }
.stat-row { display: flex; gap: 12px; margin-bottom: 1rem; flex-wrap: wrap; }
.stat-card { background: var(--color-background-secondary); border-radius: var(--border-radius-md); padding: 12px 16px; flex: 1; min-width: 100px; }
.stat-val { font-size: 22px; font-weight: 500; color: var(--color-text-primary); }
.stat-label { font-size: 12px; color: var(--color-text-secondary); margin-top: 2px; }
input[type=range] { width: 100%; }
.choice-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-top: 1rem; }
.choice-btn { border: 0.5px solid var(--color-border-secondary); border-radius: var(--border-radius-md); padding: 14px; font-size: 15px; cursor: pointer; background: none; color: var(--color-text-primary); transition: background 0.1s, border-color 0.1s; text-align: center; }
.choice-btn:hover { background: var(--color-background-secondary); }
.choice-btn.correct { border-color: #1D9E75; background: #E1F5EE; color: #085041; }
.choice-btn.wrong { border-color: #E24B4A; background: #FCEBEB; color: #501313; }
.progress-bar-wrap { background: var(--color-background-secondary); border-radius: 99px; height: 8px; overflow: hidden; margin: 8px 0; }
.progress-bar { height: 8px; border-radius: 99px; background: #1D9E75; transition: width 0.4s; }
.result-big { font-size: 36px; font-weight: 500; margin: 1rem 0 4px; color: var(--color-text-primary); }
.badge { display: inline-block; font-size: 12px; padding: 3px 10px; border-radius: var(--border-radius-md); background: var(--color-background-info); color: var(--color-text-info); margin-bottom: 8px; }
.word-display { font-size: 36px; font-weight: 500; letter-spacing: 8px; color: var(--color-text-primary); margin: 1rem 0; font-family: var(--font-mono); }
.letters-row { display: flex; flex-wrap: wrap; gap: 8px; margin: 1rem 0; }
.letter-btn { width: 38px; height: 38px; border: 0.5px solid var(--color-border-secondary); border-radius: var(--border-radius-md); font-size: 16px; cursor: pointer; background: none; color: var(--color-text-primary); transition: background 0.1s; }
.letter-btn:hover:not(:disabled) { background: var(--color-background-secondary); }
.letter-btn:disabled { opacity: 0.35; cursor: default; }
.hangman-svg { margin: 8px 0; }
.type-input { width: 100%; font-size: 22px; padding: 10px 14px; border: 0.5px solid var(--color-border-secondary); border-radius: var(--border-radius-md); background: var(--color-background-secondary); color: var(--color-text-primary); margin: 8px 0; font-family: var(--font-sans); text-align: center; }
.type-input:focus { outline: none; border-color: var(--color-border-primary); }
.reaction-box { width: 100%; height: 180px; border-radius: var(--border-radius-lg); border: 0.5px solid var(--color-border-tertiary); display: flex; align-items: center; justify-content: center; font-size: 22px; font-weight: 500; cursor: pointer; transition: background 0.1s; color: var(--color-text-primary); user-select: none; }
.reaction-box.waiting { background: var(--color-background-secondary); }
.reaction-box.ready { background: #E1F5EE; color: #085041; font-size: 26px; }
.reaction-box.early { background: #FCEBEB; color: #501313; }
.msg { font-size: 14px; color: var(--color-text-secondary); margin-top: 8px; line-height: 1.5; }
.fill-bar-row { display: flex; align-items: center; gap: 10px; margin: 6px 0; font-size: 13px; color: var(--color-text-secondary); }
.fill-bar { flex: 1; height: 14px; border-radius: 99px; background: var(--color-background-secondary); overflow: hidden; }
.fill-bar-inner { height: 14px; border-radius: 99px; background: #534AB7; transition: width 0.5s; }
</style>

<div id="hub">
<h2 class="sr-only">Fun mini-games hub — pick a game to play</h2>
<h1 class="site-title">tiny fun</h1>
<p class="site-sub">six weird little games</p>
<div class="game-grid">
  <div class="game-card" onclick="openGame('reaction')">
    <div class="icon">⚡</div>
    <div class="name">Reaction time</div>
    <div class="desc">How fast are your reflexes?</div>
  </div>
  <div class="game-card" onclick="openGame('number')">
    <div class="icon">🔢</div>
    <div class="name">Number sense</div>
    <div class="desc">Is it prime? Factor it fast.</div>
  </div>
  <div class="game-card" onclick="openGame('hangman')">
    <div class="icon">🔤</div>
    <div class="name">Word rescue</div>
    <div class="desc">Classic hangman with a twist.</div>
  </div>
  <div class="game-card" onclick="openGame('lifestat')">
    <div class="icon">❤️</div>
    <div class="name">Life in numbers</div>
    <div class="desc">How much have you lived?</div>
  </div>
  <div class="game-card" onclick="openGame('typerace')">
    <div class="icon">⌨️</div>
    <div class="name">Type racer</div>
    <div class="desc">How many WPM can you hit?</div>
  </div>
  <div class="game-card" onclick="openGame('votes')">
    <div class="icon">🌍</div>
    <div class="name">World opinions</div>
    <div class="desc">What do YOU think vs others?</div>
  </div>
</div>
</div>

<div id="game-container">
  <button class="back-btn" onclick="goHome()"><i class="ti ti-arrow-left" aria-hidden="true"></i> all games</button>
  <div id="game-area"></div>
</div>

<script>
const games = {
  reaction: {
    title: 'Reaction time',
    subtitle: 'Tap when the box turns green',
    render() {
      let state = 'idle', t0, times = [], timer;
      const div = document.createElement('div');
      div.innerHTML = `<div class="stat-row" id="rt-stats" style="display:none"></div><div id="rt-box" class="reaction-box waiting">tap to start</div><p class="msg" id="rt-msg"></p>`;
      document.getElementById('game-area').appendChild(div);
      const box = div.querySelector('#rt-box');
      const msg = div.querySelector('#rt-msg');
      const stats = div.querySelector('#rt-stats');
      box.onclick = () => {
        if(state==='idle'||state==='result'){
          state='waiting'; box.className='reaction-box waiting'; box.textContent='wait for green…'; msg.textContent='';
          clearTimeout(timer);
          timer = setTimeout(()=>{state='go';box.className='reaction-box ready';box.textContent='NOW!';t0=Date.now();},1500+Math.random()*2500);
        } else if(state==='waiting'){
          state='result'; clearTimeout(timer); box.className='reaction-box early'; box.textContent='too early! tap to retry'; msg.textContent='';
        } else if(state==='go'){
          const ms=Date.now()-t0; times.push(ms); state='result';
          box.className='reaction-box waiting'; box.textContent='tap to try again';
          msg.textContent=`${ms}ms — ${ms<200?'elite reflexes!':ms<300?'pretty fast!':ms<450?'average human':ms<600?'a bit slow':'were you asleep? 😅'}`;
          if(times.length>1){
            const avg=Math.round(times.reduce((a,b)=>a+b)/times.length);
            const best=Math.min(...times);
            stats.style.display='flex';
            stats.innerHTML=`<div class="stat-card"><div class="stat-val">${ms}ms</div><div class="stat-label">this try</div></div><div class="stat-card"><div class="stat-val">${best}ms</div><div class="stat-label">best</div></div><div class="stat-card"><div class="stat-val">${avg}ms</div><div class="stat-label">avg (${times.length} tries)</div></div>`;
          }
        }
      };
    }
  },

  number: {
    title: 'Number sense',
    subtitle: 'Is the number prime? Answer fast.',
    render() {
      function isPrime(n){if(n<2)return false;if(n===2)return true;if(n%2===0)return false;for(let i=3;i*i<=n;i+=2)if(n%i===0)return false;return true;}
      let score=0,total=0,streak=0,bestStreak=0,num,startTime,interval;
      const div=document.createElement('div');
      div.innerHTML=`<div class="stat-row"><div class="stat-card"><div class="stat-val" id="ns-score">0</div><div class="stat-label">score</div></div><div class="stat-card"><div class="stat-val" id="ns-streak">0</div><div class="stat-label">streak</div></div><div class="stat-card"><div class="stat-val" id="ns-pct">—</div><div class="stat-label">accuracy</div></div></div><div style="text-align:center;margin:1.5rem 0"><div class="big-num" id="ns-num">—</div><div class="big-label" id="ns-hint"></div><div class="progress-bar-wrap" style="margin:1rem 0"><div class="progress-bar" id="ns-timer" style="width:100%;background:#534AB7;transition:width 0.05s linear"></div></div></div><div class="choice-grid"><button class="choice-btn" id="ns-yes">✓ prime</button><button class="choice-btn" id="ns-no">✗ not prime</button></div><p class="msg" id="ns-msg" style="margin-top:1rem"></p>`;
      document.getElementById('game-area').appendChild(div);
      function newRound(){
        num=Math.floor(Math.random()*197)+2;
        div.querySelector('#ns-num').textContent=num;
        div.querySelector('#ns-hint').textContent='';
        div.querySelector('#ns-msg').textContent='';
        ['#ns-yes','#ns-no'].forEach(s=>{div.querySelector(s).className='choice-btn';div.querySelector(s).disabled=false;});
        startTime=Date.now();
        clearInterval(interval);
        const bar=div.querySelector('#ns-timer');
        bar.style.width='100%';
        interval=setInterval(()=>{const pct=Math.max(0,1-(Date.now()-startTime)/5000);bar.style.width=(pct*100)+'%';if(pct<=0){clearInterval(interval);answer(null);}},50);
      }
      function answer(choice){
        clearInterval(interval);
        const prime=isPrime(num); total++;
        const correct=(choice===true&&prime)||(choice===false&&!prime);
        if(correct){score++;streak++;bestStreak=Math.max(streak,bestStreak);}else{streak=0;}
        div.querySelector('#ns-score').textContent=score;
        div.querySelector('#ns-streak').textContent=streak+(streak===bestStreak&&bestStreak>1?' 🔥':'');
        div.querySelector('#ns-pct').textContent=Math.round(score/total*100)+'%';
        const yb=div.querySelector('#ns-yes'),nb=div.querySelector('#ns-no');
        yb.disabled=nb.disabled=true;
        if(prime){yb.className='choice-btn correct';}else{nb.className='choice-btn correct';}
        if(choice!==null&&!correct){(choice?yb:nb).className='choice-btn wrong';}
        const factors=[];for(let i=2;i<=num;i++)if(num%i===0)factors.push(i);
        div.querySelector('#ns-hint').textContent=prime?`${num} is prime`:`${num} = ${factors.slice(0,-1).join(' × ')}${factors.length>1?' × '+factors[factors.length-1]:''}`;
        div.querySelector('#ns-msg').textContent=choice===null?'time\'s up!':correct?'correct!':'wrong';
        setTimeout(newRound,1100);
      }
      div.querySelector('#ns-yes').onclick=()=>answer(true);
      div.querySelector('#ns-no').onclick=()=>answer(false);
      newRound();
    }
  },

  hangman: {
    title: 'Word rescue',
    subtitle: 'Guess the word before the stick figure falls',
    render() {
      const words=[{w:'GALAXY',h:'outer space'},{ w:'WHISPER',h:'quiet sound'},{w:'FJORD',h:'narrow inlet'},{w:'QUARTZ',h:'a crystal'},{w:'SPHINX',h:'Egyptian monument'},{w:'RHYTHM',h:'musical beat'},{w:'OXYGEN',h:'you breathe it'},{w:'VELVET',h:'a fabric'},{w:'COBALT',h:'a blue pigment'},{w:'ZENITH',h:'highest point'}];
      let word,hint,guessed,wrong,maxWrong=6;
      const div=document.createElement('div');
      div.innerHTML=`<div style="display:flex;gap:16px;align-items:flex-start;flex-wrap:wrap"><svg class="hangman-svg" width="110" height="130" viewBox="0 0 110 130" id="hm-svg"></svg><div style="flex:1;min-width:160px"><p id="hm-hint" style="font-size:13px;color:var(--color-text-secondary);margin-bottom:8px"></p><div class="word-display" id="hm-word"></div><p id="hm-status" class="msg"></p></div></div><div class="letters-row" id="hm-letters"></div><button class="game-btn" id="hm-new">new word</button>`;
      document.getElementById('game-area').appendChild(div);
      function drawHangman(n){
        const parts=[
          '<line x1="10" y1="125" x2="100" y2="125" stroke="var(--color-border-primary)" stroke-width="2"/>',
          '<line x1="30" y1="125" x2="30" y2="10" stroke="var(--color-border-primary)" stroke-width="2"/>',
          '<line x1="30" y1="10" x2="70" y2="10" stroke="var(--color-border-primary)" stroke-width="2"/>',
          '<line x1="70" y1="10" x2="70" y2="25" stroke="var(--color-border-primary)" stroke-width="2"/>',
          '<circle cx="70" cy="35" r="10" stroke="var(--color-text-secondary)" stroke-width="2" fill="none"/>',
          '<line x1="70" y1="45" x2="70" y2="80" stroke="var(--color-text-secondary)" stroke-width="2"/>',
          '<line x1="70" y1="55" x2="55" y2="70" stroke="var(--color-text-secondary)" stroke-width="2"/>',
          '<line x1="70" y1="55" x2="85" y2="70" stroke="var(--color-text-secondary)" stroke-width="2"/>',
          '<line x1="70" y1="80" x2="55" y2="100" stroke="var(--color-text-secondary)" stroke-width="2"/>',
          '<line x1="70" y1="80" x2="85" y2="100" stroke="var(--color-text-secondary)" stroke-width="2"/>',
        ];
        div.querySelector('#hm-svg').innerHTML=parts.slice(0,n+4).join('');
      }
      function startGame(){
        const pick=words[Math.floor(Math.random()*words.length)];
        word=pick.w; hint=pick.h; guessed=new Set(); wrong=0;
        div.querySelector('#hm-hint').textContent='hint: '+hint;
        render();
      }
      function render(){
        const display=word.split('').map(c=>guessed.has(c)?c:'_').join(' ');
        div.querySelector('#hm-word').textContent=display;
        drawHangman(wrong);
        const won=word.split('').every(c=>guessed.has(c));
        const lost=wrong>=maxWrong;
        div.querySelector('#hm-status').textContent=won?'you saved them! 🎉':lost?'word was: '+word:'wrong: '+wrong+'/'+maxWrong;
        const lrow=div.querySelector('#hm-letters');
        lrow.innerHTML='';
        'ABCDEFGHIJKLMNOPQRSTUVWXYZ'.split('').forEach(l=>{
          const b=document.createElement('button');
          b.className='letter-btn'; b.textContent=l;
          if(guessed.has(l)||won||lost)b.disabled=true;
          b.onclick=()=>{guessed.add(l);if(!word.includes(l))wrong++;render();};
          lrow.appendChild(b);
        });
      }
      div.querySelector('#hm-new').onclick=startGame;
      startGame();
    }
  },

  lifestat: {
    title: 'Life in numbers',
    subtitle: 'Enter your birthday and see your life stats',
    render() {
      const div=document.createElement('div');
      div.innerHTML=`<div style="margin-bottom:1rem"><label style="font-size:13px;color:var(--color-text-secondary)">your birthday</label><br><input type="date" id="ls-date" style="margin-top:6px;padding:8px 12px;border:0.5px solid var(--color-border-secondary);border-radius:var(--border-radius-md);background:var(--color-background-secondary);color:var(--color-text-primary);font-size:15px;width:100%;max-width:260px"></div><div id="ls-out" style="display:none"><div class="stat-row" id="ls-stats"></div><div id="ls-bars" style="margin-top:1rem"></div></div>`;
      document.getElementById('game-area').appendChild(div);
      const inp=div.querySelector('#ls-date');
      const d=new Date(); d.setFullYear(d.getFullYear()-25);
      inp.value=d.toISOString().split('T')[0];
      inp.max=new Date().toISOString().split('T')[0];
      inp.oninput=calc;
      function calc(){
        const bd=new Date(inp.value); if(isNaN(bd))return;
        const now=new Date();
        const diffMs=now-bd; if(diffMs<0)return;
        const secs=Math.floor(diffMs/1000);
        const mins=Math.floor(secs/60);
        const hrs=Math.floor(mins/60);
        const days=Math.floor(hrs/24);
        const years=now.getFullYear()-bd.getFullYear()-(now<new Date(now.getFullYear(),bd.getMonth(),bd.getDate())?1:0);
        const hearts=Math.round(secs*1.2);
        const breaths=Math.round(secs*0.25);
        const sleepDays=Math.round(days*0.33);
        const lifeExpect=79;
        const pctLived=Math.min(100,Math.round(years/lifeExpect*100));
        div.querySelector('#ls-out').style.display='block';
        div.querySelector('#ls-stats').innerHTML=`
          <div class="stat-card"><div class="stat-val">${years.toLocaleString()}</div><div class="stat-label">years</div></div>
          <div class="stat-card"><div class="stat-val">${days.toLocaleString()}</div><div class="stat-label">days</div></div>
          <div class="stat-card"><div class="stat-val">${hrs.toLocaleString()}</div><div class="stat-label">hours</div></div>`;
        div.querySelector('#ls-bars').innerHTML=`
          <p style="font-size:13px;color:var(--color-text-secondary);margin-bottom:8px">milestones</p>
          ${bar('heartbeats',hearts.toLocaleString())}
          ${bar('breaths taken',breaths.toLocaleString())}
          ${bar('days asleep',sleepDays.toLocaleString())}
          ${bar('life lived (avg 79yr)',pctLived+'%',pctLived)}`;
      }
      function bar(label,val,pct){
        pct=pct??100;
        return `<div class="fill-bar-row"><span style="min-width:140px">${label}</span><div class="fill-bar"><div class="fill-bar-inner" style="width:${Math.min(100,pct)}%"></div></div><span style="min-width:80px;text-align:right;font-size:13px;color:var(--color-text-primary)">${val}</span></div>`;
      }
      calc();
    }
  },

  typerace: {
    title: 'Type racer',
    subtitle: 'Type the sentence as fast as you can',
    render() {
      const sentences=[
        'The quick brown fox jumps over the lazy dog',
        'Pack my box with five dozen liquor jugs',
        'How vexingly quick daft zebras jump',
        'Bright vixens jump; dozy fowl quack',
        'Sphinx of black quartz judge my vow',
        'The five boxing wizards jump quickly',
        'Cozy lummox gives smart squid who asks for job pen',
        'Waltz nymph for quick jigs vex bud',
      ];
      let target,startTime,started=false,finished=false;
      const div=document.createElement('div');
      div.innerHTML=`<div id="tr-target" style="font-size:18px;line-height:1.7;color:var(--color-text-secondary);border:0.5px solid var(--color-border-tertiary);border-radius:var(--border-radius-md);padding:12px 16px;margin-bottom:12px;font-family:var(--font-mono)"></div><input class="type-input" id="tr-input" placeholder="start typing..." autocomplete="off" autocorrect="off" spellcheck="false"><div class="stat-row" id="tr-results" style="display:none;margin-top:1rem"></div><button class="game-btn" id="tr-new">new sentence</button>`;
      document.getElementById('game-area').appendChild(div);
      function newGame(){
        target=sentences[Math.floor(Math.random()*sentences.length)];
        started=false; finished=false;
        div.querySelector('#tr-input').value='';
        div.querySelector('#tr-input').disabled=false;
        div.querySelector('#tr-input').focus();
        div.querySelector('#tr-results').style.display='none';
        renderTarget('');
      }
      function renderTarget(typed){
        const tgt=div.querySelector('#tr-target');
        let html='';
        for(let i=0;i<target.length;i++){
          const ch=target[i];
          if(i<typed.length){
            html+=`<span style="color:${typed[i]===ch?'var(--color-text-primary)':'#E24B4A'};text-decoration:${typed[i]===ch?'none':'underline'}">${ch==' '?'&nbsp;':ch}</span>`;
          } else if(i===typed.length){
            html+=`<span style="background:var(--color-background-secondary)">${ch==' '?'&nbsp;':ch}</span>`;
          } else {
            html+=`<span style="color:var(--color-text-tertiary)">${ch==' '?'&nbsp;':ch}</span>`;
          }
        }
        tgt.innerHTML=html;
      }
      div.querySelector('#tr-input').oninput=function(){
        if(finished)return;
        const val=this.value;
        if(!started&&val.length>0){started=true;startTime=Date.now();}
        renderTarget(val);
        if(val===target){
          finished=true; this.disabled=true;
          const elapsed=(Date.now()-startTime)/1000;
          const words=target.split(' ').length;
          const wpm=Math.round(words/(elapsed/60));
          const errors=val.split('').filter((c,i)=>c!==target[i]).length;
          const acc=Math.round((1-errors/target.length)*100);
          div.querySelector('#tr-results').style.display='flex';
          div.querySelector('#tr-results').innerHTML=`<div class="stat-card"><div class="stat-val">${wpm}</div><div class="stat-label">WPM</div></div><div class="stat-card"><div class="stat-val">${elapsed.toFixed(1)}s</div><div class="stat-label">time</div></div><div class="stat-card"><div class="stat-val">${acc}%</div><div class="stat-label">accuracy</div></div>`;
        }
      };
      div.querySelector('#tr-new').onclick=newGame;
      newGame();
    }
  },

  votes: {
    title: 'World opinions',
    subtitle: 'Answer a question, then see what others said',
    render() {
      const questions=[
        {q:'Would you rather live in the city or the countryside?',opts:['city','countryside'],data:[58,42]},
        {q:'Is a hot dog a sandwich?',opts:['yes','no'],data:[31,69]},
        {q:'Do you think aliens exist?',opts:['yes','no'],data:[74,26]},
        {q:'Do you prefer mornings or nights?',opts:['mornings','nights'],data:[44,56]},
        {q:'Could you go a week without the internet?',opts:['yes','no'],data:[29,71]},
        {q:'Is cereal a soup?',opts:['yes','no'],data:[22,78]},
        {q:'Do you think you could survive a zombie apocalypse?',opts:['yes','no'],data:[41,59]},
        {q:'Cats or dogs?',opts:['cats','dogs'],data:[38,62]},
      ];
      let qi=Math.floor(Math.random()*questions.length),answered=false;
      const div=document.createElement('div');
      div.innerHTML=`<p style="font-size:18px;font-weight:500;color:var(--color-text-primary);margin-bottom:1.25rem" id="vo-q"></p><div class="choice-grid" id="vo-opts"></div><div id="vo-results" style="display:none;margin-top:1.25rem"></div><button class="game-btn" id="vo-next" style="margin-top:1rem">next question</button>`;
      document.getElementById('game-area').appendChild(div);
      function loadQ(){
        answered=false;
        const q=questions[qi];
        div.querySelector('#vo-q').textContent=q.q;
        div.querySelector('#vo-results').style.display='none';
        const og=div.querySelector('#vo-opts'); og.innerHTML='';
        q.opts.forEach((opt,i)=>{
          const b=document.createElement('button'); b.className='choice-btn'; b.textContent=opt;
          b.onclick=()=>{
            if(answered)return; answered=true;
            const chosen=i; const other=1-i;
            const res=div.querySelector('#vo-results'); res.style.display='block';
            const total=q.data[0]+q.data[1];
            const pcts=q.data.map(v=>Math.round(v/total*100));
            res.innerHTML=`<p style="font-size:13px;color:var(--color-text-secondary);margin-bottom:10px">you said <strong>${opt}</strong> — here's what others think:</p>`+
              q.opts.map((o,j)=>`<div class="fill-bar-row"><span style="min-width:100px">${o}</span><div class="fill-bar"><div class="fill-bar-inner" style="width:${pcts[j]}%;background:${j===chosen?'#534AB7':'#9FE1CB'}"></div></div><span style="min-width:40px;text-align:right;font-size:13px;color:var(--color-text-primary)">${pcts[j]}%</span></div>`).join('');
            og.querySelectorAll('.choice-btn').forEach((bb,j)=>bb.className='choice-btn'+(j===chosen?' correct':''));
          };
          og.appendChild(b);
        });
      }
      div.querySelector('#vo-next').onclick=()=>{qi=(qi+1)%questions.length;loadQ();};
      loadQ();
    }
  }
};

function openGame(id){
  document.getElementById('hub').style.display='none';
  const gc=document.getElementById('game-container');
  gc.style.display='block';
  const ga=document.getElementById('game-area');
  ga.innerHTML=`<div class="game-title">${games[id].title}</div><div class="game-subtitle">${games[id].subtitle}</div>`;
  games[id].render();
}

function goHome(){
  document.getElementById('hub').style.display='block';
  document.getElementById('game-container').style.display='none';
  document.getElementById('game-area').innerHTML='';
}
</script>
