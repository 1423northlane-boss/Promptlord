# Promptlord
Code
"use client";

import React, { useState } from 'react';
import { Shield, Lock, Cpu, Zap, ArrowRight, BarChart3, Globe } from 'lucide-react';
import { signIn, useSession } from "next-auth/react";

export default function PromptLordFinal() {
  const { data: session } = useSession();
  const [isAnalyzing, setIsAnalyzing] = useState(false);
  const [ltv, setLtv] = useState(70);

  return (
    <div className="min-h-screen bg-[#010101] text-[#FACC15] font-sans selection:bg-[#FACC15] selection:text-black">
      
      {/* --- TOP SECURE PROTOCOL NAV --- */}
      <nav className="p-6 border-b border-[#FACC15]/10 flex justify-between items-center sticky top-0 bg-[#010101]/95 backdrop-blur-md z-50">
        <div className="flex items-center gap-3">
          <div className="w-10 h-10 border-2 border-[#FACC15] rounded-full flex items-center justify-center animate-pulse">
            <Lock size={18} />
          </div>
          <h1 className="text-2xl font-black tracking-tighter uppercase">PROMPTLORD</h1>
        </div>
        <button 
          onClick={() => signIn('google')}
          className="bg-[#FACC15] text-black px-6 py-2 font-black text-xs hover:bg-white transition-all tracking-widest shadow-[0_0_20px_rgba(250,204,21,0.2)]"
        >
          {session ? `LOGGED IN: ${session.user?.name?.toUpperCase()}` : "ACCESS SECURE PORTAL"}
        </button>
      </nav>

      <main className="max-w-6xl mx-auto px-6 py-20">
        
        {/* --- HERO: THE NIGHTWING IDENTITY --- */}
        <div className="text-center mb-32">
          <div className="inline-block border border-[#FACC15]/40 px-4 py-1 text-[10px] font-bold tracking-[0.4em] mb-8 bg-[#FACC15]/5">
            DECENTRALIZED RWA INFRASTRUCTURE
          </div>
          <h2 className="text-8xl md:text-9xl font-black text-white leading-none mb-6 tracking-tighter">
            THE <span className="text-[#FACC15]">VOID</span> <br/>YIELDS.
          </h2>
          <p className="text-[#CA8A04] font-mono text-sm tracking-widest uppercase italic mb-12">
            "I am the liquidity that flows in the night. I am the PROMPTLORD."
          </p>
          <div className="flex justify-center gap-12 text-[#FACC15]/40 font-bold text-[10px]">
            <span className="flex items-center gap-2"><Globe size={14}/> UD RESOLVED: PROMPTLORD.CRYPTO</span>
            <span className="flex items-center gap-2"><Shield size={14}/> 1% SOLE AFFILIATE PROTECTED</span>
          </div>
        </div>

        {/* --- THE GEMINI QUANTUM ORACLE --- */}
        <section className="grid lg:grid-cols-2 gap-12 mb-32">
          <div className="bg-[#050505] border border-[#FACC15]/20 p-8 rounded-sm relative overflow-hidden group">
            <div className="absolute top-0 right-0 p-4 opacity-10 group-hover:opacity-100 transition-opacity">
               <Cpu size={40} />
            </div>
            <h3 className="text-xl font-black mb-6 flex items-center gap-2">
              <Zap size={20} /> GEMINI_ORACLE_v2
            </h3>
            <p className="text-xs text-white/60 mb-8 leading-relaxed">
              Input property financials for a Quantum Risk Assessment. 
              The Oracle calculates LTV, yield compression, and tokenization feasibility.
            </p>
            <input 
              type="text" 
              placeholder="Paste Real Estate Portfolio Data..." 
              className="w-full bg-black border border-[#FACC15]/30 p-4 text-sm text-[#FACC15] outline-none focus:border-[#FACC15] mb-4"
            />
            <button 
              onClick={() => setIsAnalyzing(true)}
              className="w-full py-4 border-2 border-[#FACC15] font-black uppercase tracking-widest hover:bg-[#FACC15] hover:text-black transition-all"
            >
              {isAnalyzing ? "Processing Quantum Data..." : "Consult the Oracle"}
            </button>
          </div>

          {/* --- MONETARY GAIN MONITOR --- */}
          <div className="bg-[#FACC15] p-8 text-black flex flex-col justify-between">
            <div>
              <h3 className="text-2xl font-black mb-2 uppercase">Affiliate Vault</h3>
              <p className="text-[10px] font-bold uppercase opacity-60">Revenue generated via 1% Protocol Fee</p>
            </div>
            <div className="my-8">
              <p className="text-6xl font-black tracking-tighter">$128,440.00</p>
              <p className="text-xs font-bold uppercase">Ready for Withdrawal</p>
            </div>
            <button className="w-full py-4 bg-black text-[#FACC15] font-black uppercase text-xs tracking-widest hover:bg-neutral-900 transition-all">
              Withdraw to Affiliate Wallet
            </button>
          </div>
        </section>

        {/* --- RWA LTV CALCULATOR --- */}
        <section className="border-t border-[#FACC15]/10 pt-20">
          <div className="flex flex-col md:flex-row justify-between items-end mb-12">
            <h2 className="text-4xl font-black uppercase tracking-tighter">LTV Intelligence</h2>
            <div className="text-right">
               <p className="text-[10px] text-white/40 font-bold">CURRENT_MARKET_CAP_RATE</p>
               <p className="text-xl font-bold">5.82%</p>
            </div>
          </div>
          
          <div className="bg-[#050505] p-10 border border-[#FACC15]/10">
            <input 
              type="range" min="0" max="100" value={ltv}
              onChange={(e) => setLtv(Number(e.target.value))}
              className="w-full h-1 bg-[#222] appearance-none cursor-pointer accent-[#FACC15] mb-8"
            />
            <div className="flex justify-between font-mono">
              <div>
                <p className="text-[10px] opacity-40">LOAN-TO-VALUE</p>
                <p className="text-4xl font-black">{ltv}%</p>
              </div>
              <div className="text-right">
                <p className="text-[10px] opacity-40">RISK_RATING</p>
                <p className={`text-4xl font-black ${ltv > 75 ? 'text-red-600' : 'text-green-500'}`}>
                  {ltv > 75 ? 'HIGH' : 'OPTIMAL'}
                </p>
              </div>
            </div>
          </div>
        </section>
      </main>

      <footer className="p-10 text-center border-t border-[#FACC15]/10 bg-[#030303]">
        <p className="text-[10px] font-black tracking-[0.6em] text-[#CA8A04] opacity-50 uppercase">
          PROMPTLORD PROTOCOL | UD_RESOLVED | ALL_RIGHTS_RESERVED_2026
        </p>
      </footer>
    </div>
  );
}
