import React, { useState, useEffect, useRef, useMemo } from 'react';
import { Hammer, History, Share2, Trash2, Zap, Award, Box, Download, X, Smartphone } from 'lucide-react';

// --- 全局设计配置 ---
const THEME = {
  cyan: '#00FFD1',
  pink: '#FF2E63',
  bg: '#050510',
};

// --- 1. 粒子星云背景引擎 (Canvas) ---
const NebulaBackground = () => {
  const canvasRef = useRef(null);

  useEffect(() => {
    const canvas = canvasRef.current;
    const ctx = canvas.getContext('2d');
    let animationFrameId;
    let particles = [];

    const resize = () => {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
    };

    class Particle {
      constructor() {
        this.x = Math.random() * canvas.width;
        this.y = Math.random() * canvas.height;
        this.size = Math.random() * 2;
        this.speedX = Math.random() * 0.5 - 0.25;
        this.speedY = Math.random() * 0.5 - 0.25;
        this.color = Math.random() > 0.5 ? THEME.cyan : THEME.pink;
        this.alpha = Math.random() * 0.5;
      }

      update() {
        this.x += this.speedX;
        this.y += this.speedY;
        if (this.size > 0.2) this.alpha -= 0.001;
        if (this.alpha <= 0) {
          this.x = Math.random() * canvas.width;
          this.y = Math.random() * canvas.height;
          this.alpha = 0.5;
        }
        // 边界检查
        if (this.x < 0 || this.x > canvas.width) this.speedX *= -1;
        if (this.y < 0 || this.y > canvas.height) this.speedY *= -1;
      }

      draw() {
        ctx.fillStyle = this.color;
        ctx.globalAlpha = this.alpha;
        ctx.beginPath();
        ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
        ctx.fill();
      }
    }

    const init = () => {
      particles = [];
      for (let i = 0; i < 60; i++) {
        particles.push(new Particle());
      }
    };

    const animate = () => {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      
      // 绘制深空渐变背景
      const gradient = ctx.createLinearGradient(0, 0, canvas.width, canvas.height);
      gradient.addColorStop(0, '#050510');
      gradient.addColorStop(0.5, '#0a0a1a');
      gradient.addColorStop(1, '#050510');
      ctx.fillStyle = gradient;
      ctx.fillRect(0, 0, canvas.width, canvas.height);

      particles.forEach(p => {
        p.update();
        p.draw();
      });
      animationFrameId = requestAnimationFrame(animate);
    };

    window.addEventListener('resize', resize);
    resize();
    init();
    animate();

    return () => {
      window.removeEventListener('resize', resize);
      cancelAnimationFrame(animationFrameId);
    };
  }, []);

  return (
    <canvas 
      ref={canvasRef} 
      className="fixed top-0 left-0 w-full h-full pointer-events-none z-0"
    />
  );
};

// --- 2. 液态金属按钮 (SVG Gooey Filter) ---
const MoltenButton = ({ isRecording, toggleRecording }) => {
  return (
    <div className="relative flex items-center justify-center w-32 h-32">
      {/* SVG 滤镜定义 */}
      <svg className="absolute w-0 h-0">
        <defs>
          <filter id="goo">
            <feGaussianBlur in="SourceGraphic" stdDeviation="10" result="blur" />
            <feColorMatrix in="blur" mode="matrix" values="1 0 0 0 0  0 1 0 0 0  0 0 1 0 0  0 0 0 18 -7" result="goo" />
            <feBlend in="SourceGraphic" in2="goo" />
          </filter>
        </defs>
      </svg>

      {/* 外部光晕圆环 */}
      <div 
        className={`absolute w-full h-full rounded-full border-2 border-cyan-400/30 animate-spin-slow transition-opacity duration-500 ${isRecording ? 'opacity-100' : 'opacity-30'}`}
        style={{ animationDuration: '8s' }}
      ></div>
      <div 
        className={`absolute w-[110%] h-[110%] rounded-full border border-pink-500/20 animate-spin-reverse transition-opacity duration-500 ${isRecording ? 'opacity-100' : 'opacity-20'}`}
        style={{ animationDuration: '12s' }}
      ></div>

      {/* 液态核心按钮 */}
      <button
        onClick={toggleRecording}
        className="relative z-10 group focus:outline-none"
        style={{ filter: 'url(#goo)' }} // 应用液态滤镜
      >
        <div className={`
          relative flex items-center justify-center
          w-20 h-20 rounded-full 
          bg-gradient-to-br from-cyan-400 via-white to-pink-500
          transition-all duration-700 ease-in-out
          ${isRecording ? 'scale-90 animate-pulse' : 'scale-100 hover:scale-110'}
          shadow-[0_0_30px_rgba(0,255,209,0.4)]
        `}>
           {/* 内部流体层 */}
           <div className="absolute inset-0 bg-white/50 rounded-full blur-md transform scale-75 opacity-50"></div>
           
           <div className={`transition-transform duration-500 ${isRecording ? 'rotate-180' : 'rotate-0'}`}>
             {isRecording ? (
               <div className="w-6 h-6 bg-black rounded-sm" />
             ) : (
               <div className="w-0 h-0 border-l-[12px] border-l-black border-y-[8px] border-y-transparent ml-1" />
             )}
           </div>
        </div>
        
        {/* 粒子飞溅效果 (Visual Only) */}
        {isRecording && (
          <>
            <div className="absolute top-0 left-0 w-20 h-20 bg-cyan-400 rounded-full animate-ping opacity-20"></div>
            <div className="absolute top-0 left-0 w-20 h-20 bg-pink-500 rounded-full animate-ping opacity-20" style={{ animationDelay: '0.5s'}}></div>
          </>
        )}
      </button>
    </div>
  );
};

// --- 3. 水晶棱镜卡片 (Glassmorphism) ---
const CrystalCard = ({ session, onDelete }) => {
  const formatTime = (seconds) => {
    const h = Math.floor(seconds / 3600).toString().padStart(2, '0');
    const m = Math.floor((seconds % 3600) / 60).toString().padStart(2, '0');
    const s = (seconds % 60).toString().padStart(2, '0');
    return `${h}:${m}:${s}`;
  };

  return (
    <div className="group relative w-full mb-6 perspective-1000">
      {/* 3D 倾斜容器 */}
      <div className="relative w-full p-6 rounded-3xl overflow-hidden transition-transform duration-500 hover:rotate-x-2 transform-style-3d">
        
        {/* 磨砂背景层 */}
        <div className="absolute inset-0 bg-white/5 backdrop-blur-xl border border-white/10 shadow-2xl rounded-3xl"></div>
        
        {/* 霓虹光边 (Hover显现) */}
        <div className="absolute inset-0 rounded-3xl border border-cyan-400/0 group-hover:border-cyan-400/30 transition-colors duration-500 pointer-events-none"></div>
        
        {/* 内容 */}
        <div className="relative z-10 flex justify-between items-center">
          <div className="flex flex-col space-y-2">
             <div className="flex items-center space-x-2 text-cyan-300/80 text-xs uppercase tracking-widest font-semibold">
               <Hammer size={14} />
               <span>{session.date}</span>
             </div>
             <div className="text-5xl font-thin text-transparent bg-clip-text bg-gradient-to-r from-white via-cyan-100 to-cyan-200 font-mono tracking-tighter drop-shadow-[0_0_10px_rgba(0,255,209,0.3)]">
               {formatTime(session.duration)}
             </div>
             <div className="flex items-center space-x-3 text-xs text-white/40">
               <span className="flex items-center space-x-1">
                 <Zap size={12} /> 
                 <span>{session.taps} 次</span>
               </span>
               <span>•</span>
               <span>{session.type}</span>
             </div>
          </div>

          {/* 删除按钮 */}
          <button 
            onClick={() => onDelete(session.id)}
            className="p-3 rounded-full hover:bg-white/10 text-white/30 hover:text-red-400 transition-colors"
          >
            <Trash2 size={18} />
          </button>
        </div>

        {/* 装饰性反光 */}
        <div className="absolute -top-20 -right-20 w-40 h-40 bg-gradient-to-br from-white/10 to-transparent rounded-full blur-2xl pointer-events-none"></div>
      </div>
    </div>
  );
};

// --- 4. 安装引导弹窗 (Install Modal) ---
const InstallModal = ({ onClose }) => {
  return (
    <div className="fixed inset-0 z-50 flex items-center justify-center p-6">
      <div className="absolute inset-0 bg-black/80 backdrop-blur-sm" onClick={onClose}></div>
      <div className="relative w-full max-w-sm bg-[#121220] border border-white/10 rounded-3xl p-6 shadow-2xl overflow-hidden">
        {/* 装饰背景 */}
        <div className="absolute top-0 left-0 w-full h-1 bg-gradient-to-r from-cyan-400 to-pink-500"></div>
        <div className="absolute -top-20 -right-20 w-40 h-40 bg-cyan-500/20 rounded-full blur-3xl"></div>
        
        <div className="relative z-10 flex flex-col items-center text-center">
          <div className="w-16 h-16 rounded-2xl bg-gradient-to-br from-cyan-400 to-pink-500 flex items-center justify-center mb-4 shadow-[0_0_20px_rgba(0,255,209,0.3)]">
             <Box className="text-white" size={32} />
          </div>
          <h2 className="text-xl font-bold text-white mb-2">安装“匠痕”到桌面</h2>
          <p className="text-white/60 text-sm mb-6 leading-relaxed">
            将此 Web App 添加到主屏幕，获得全屏沉浸式体验，享受如原生应用般的丝滑流畅。
          </p>
          
          <div className="w-full space-y-3">
            <div className="flex items-center p-3 bg-white/5 rounded-xl border border-white/5">
               <div className="p-2 bg-white/10 rounded-lg mr-3"><Share2 size={18} className="text-cyan-400"/></div>
               <div className="text-left text-sm text-white/80">
                 1. 点击浏览器底部的 <span className="text-white font-bold">分享</span> 按钮
               </div>
            </div>
            <div className="flex items-center p-3 bg-white/5 rounded-xl border border-white/5">
               <div className="p-2 bg-white/10 rounded-lg mr-3"><Smartphone size={18} className="text-pink-400"/></div>
               <div className="text-left text-sm text-white/80">
                 2. 选择 <span className="text-white font-bold">添加到主屏幕</span>
               </div>
            </div>
          </div>

          <button 
            onClick={onClose}
            className="mt-6 px-8 py-2 rounded-full bg-white/10 hover:bg-white/20 text-white text-sm font-medium transition-colors"
          >
            明白了
          </button>
        </div>

        <button onClick={onClose} className="absolute top-4 right-4 text-white/30 hover:text-white">
          <X size={20} />
        </button>
      </div>
    </div>
  );
};

// --- 5. 主程序 ---
export default function App() {
  const [isRecording, setIsRecording] = useState(false);
  const [duration, setDuration] = useState(0);
  const [taps, setTaps] = useState(0);
  
  // PWA 安装逻辑
  const [deferredPrompt, setDeferredPrompt] = useState(null);
  const [showInstallModal, setShowInstallModal] = useState(false);

  const [sessions, setSessions] = useState([
    { id: 1, date: '2026.05.20', duration: 5400, taps: 124, type: '木工' },
    { id: 2, date: '2026.05.19', duration: 3200, taps: 89, type: '皮艺' },
  ]);
  
  // 点击特效状态
  const [clickEffects, setClickEffects] = useState([]);

  // 初始化：监听 PWA 安装事件 & 计时器
  useEffect(() => {
    // 1. 监听安装事件
    const handleBeforeInstallPrompt = (e) => {
      e.preventDefault(); // 阻止浏览器默认的底部横幅
      setDeferredPrompt(e);
    };
    window.addEventListener('beforeinstallprompt', handleBeforeInstallPrompt);

    // 2. 计时器
    let interval;
    if (isRecording) {
      interval = setInterval(() => {
        setDuration(prev => prev + 1);
      }, 1000);
    }
    
    return () => {
      window.removeEventListener('beforeinstallprompt', handleBeforeInstallPrompt);
      clearInterval(interval);
    };
  }, [isRecording]);

  // 触觉反馈 Helper
  const triggerHaptic = (pattern = [10]) => {
    if (navigator.vibrate) navigator.vibrate(pattern);
  };
  
  // 处理安装点击
  const handleInstallClick = () => {
    if (deferredPrompt) {
      // 如果浏览器支持原生安装 (如 Android/Chrome)
      deferredPrompt.prompt();
      deferredPrompt.userChoice.then((choiceResult) => {
        if (choiceResult.outcome === 'accepted') {
          console.log('用户接受安装');
        }
        setDeferredPrompt(null);
      });
    } else {
      // 如果是 iOS 或不支持原生提示的浏览器，显示手动引导 Modal
      setShowInstallModal(true);
    }
  };

  // 开始/结束
  const toggleRecording = (e) => {
    e.stopPropagation();
    if (isRecording) {
      // 停止
      const newSession = {
        id: Date.now(),
        date: new Date().toLocaleDateString('en-CA').replace(/-/g, '.'),
        duration: duration,
        taps: taps,
        type: '新工艺'
      };
      setSessions([newSession, ...sessions]);
      setDuration(0);
      setTaps(0);
      triggerHaptic([30, 50, 30]); // 较重的结束震动
    } else {
      // 开始
      triggerHaptic([15]); // 轻微开始震动
    }
    setIsRecording(!isRecording);
  };

  // 点击屏幕计数 (仅在录制时)
  const handleScreenTap = (e) => {
    if (!isRecording) return;

    // 增加计数
    setTaps(prev => prev + 1);
    triggerHaptic([5]); // 极短的清脆震动

    // 添加视觉特效
    const id = Date.now();
    const x = e.clientX;
    const y = e.clientY;
    
    setClickEffects(prev => [...prev, { id, x, y }]);

    // 清理特效
    setTimeout(() => {
      setClickEffects(prev => prev.filter(effect => effect.id !== id));
    }, 600);
  };

  const deleteSession = (id) => {
    setSessions(sessions.filter(s => s.id !== id));
  };

  return (
    <div 
      className="relative w-full h-screen overflow-hidden bg-[#050510] text-white font-sans selection:bg-cyan-500/30"
      onClick={handleScreenTap}
    >
      <NebulaBackground />

      {/* UI 容器 */}
      <div className="relative z-10 flex flex-col h-full max-w-md mx-auto bg-gradient-to-b from-transparent via-black/5 to-black/20">
        
        {/* 顶部 Header */}
        <div className="flex justify-between items-end p-6 pt-12 border-b border-white/5 bg-white/5 backdrop-blur-md">
          <div>
            <h1 className="text-3xl font-thin tracking-wide text-white" style={{ fontFamily: 'STSong, Georgia, serif', fontStyle: 'italic' }}>匠痕</h1>
            <p className="text-[10px] uppercase tracking-[0.3em] text-cyan-400 mt-1 opacity-80">专注 · 创造 · 超越</p>
          </div>
          <div className="flex space-x-2">
             {/* 安装按钮 */}
             <button 
               onClick={handleInstallClick}
               className="p-2 rounded-full bg-white/5 hover:bg-white/10 border border-white/10 transition-all text-cyan-400/80 hover:text-cyan-400"
             >
                <Download size={20} />
             </button>
             <button className="p-2 rounded-full bg-white/5 hover:bg-white/10 border border-white/10 transition-all">
                <Box size={20} className="text-white/70" />
             </button>
          </div>
        </div>

        {/* 中间滚动区域 (时光长河) */}
        <div className="flex-1 overflow-y-auto p-4 pb-40 scrollbar-hide">
           {sessions.map(session => (
             <CrystalCard key={session.id} session={session} onDelete={deleteSession} />
           ))}
           
           {/* 底部占位 */}
           <div className="h-24 flex items-center justify-center text-white/10 text-sm tracking-widest">
             — 时光长河尽头 —
           </div>
        </div>

        {/* 底部控制台 */}
        <div className="absolute bottom-0 left-0 w-full h-64 pointer-events-none">
           {/* 底部渐变遮罩 */}
           <div className="absolute inset-0 bg-gradient-to-t from-[#050510] via-[#050510]/90 to-transparent"></div>
           
           {/* 录制状态显示 (悬浮在按钮上方) */}
           <div className={`absolute top-0 left-0 w-full flex flex-col items-center justify-center transition-all duration-500 ${isRecording ? 'opacity-100 translate-y-10' : 'opacity-0 translate-y-20'}`}>
              <div className="text-7xl font-thin font-mono text-white drop-shadow-[0_0_15px_rgba(255,255,255,0.5)]">
                {new Date(duration * 1000).toISOString().substr(11, 8)}
              </div>
              <div className="text-cyan-400 text-sm tracking-[0.2em] mt-2 font-bold uppercase animate-pulse">
                记录中 • {taps} 次
              </div>
           </div>

           {/* 按钮容器 */}
           <div className="absolute bottom-8 left-0 w-full flex justify-center pointer-events-auto">
             <MoltenButton isRecording={isRecording} toggleRecording={toggleRecording} />
           </div>
        </div>
      </div>

      {/* 点击波纹特效层 */}
      {clickEffects.map(effect => (
        <div
          key={effect.id}
          className="absolute pointer-events-none border-2 border-white/50 rounded-full animate-ping"
          style={{
            left: effect.x,
            top: effect.y,
            width: '40px',
            height: '40px',
            transform: 'translate(-50%, -50%)',
            animationDuration: '0.4s'
          }}
        >
           {/* 十字星 */}
           <div className="absolute top-1/2 left-1/2 w-20 h-[1px] bg-cyan-400 -translate-x-1/2 -translate-y-1/2 rotate-45"></div>
           <div className="absolute top-1/2 left-1/2 w-20 h-[1px] bg-cyan-400 -translate-x-1/2 -translate-y-1/2 -rotate-45"></div>
        </div>
      ))}

      {/* 安装弹窗 */}
      {showInstallModal && <InstallModal onClose={() => setShowInstallModal(false)} />}
    </div>
  );
}
