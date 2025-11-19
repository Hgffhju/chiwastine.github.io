# chiwastine.github.i# Save as: 2049_money_quiz.py
# Run with: streamlit run 2049_money_quiz.py

import streamlit as st
import time

# Page config
st.set_page_config(page_title="2049 Money Quiz", page_icon="🚀", layout="centered")

# Custom CSS (2049 cyberpunk style)
st.markdown("""
<style>
    .big-title {font-size: 3.5rem; color: #00ffea; text-align: center; text-shadow: 0 0 20px #00ffea; font-family: 'Orbitron', sans-serif;}
    .stApp {background: #0a0e17; color: #e0e7ff;}
    .option-btn {background: #1a1f2e !important; border: 2px solid #00ffea !important; color: white !important; padding: 20px; margin: 10px 0; border-radius: 15px;}
    .option-btn:hover {background: #00ffea !important; color: black !important;}
    .selected {background: #00ffea !important; color: black !important;}
    .timer {background: #ff0066; color: white; padding: 15px; font-size: 1.8rem; text-align: center;}
    .ticker {background: rgba(255,0,102,0.9); color: white; padding: 15px; font-size: 1.3rem; overflow: hidden; white-space: nowrap; margin-bottom: 20px;}
</style>
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500;700&family=Roboto+Mono&display=swap" rel="stylesheet">
""", unsafe_allow_html=True)

# Live ticker messages
ticker_messages = [
    "Sarah from USA just got $100k funded account (2 min ago)",
    "Michael from UK started faceless YouTube empire (4 min ago)",
    "Alex from Canada claimed ySense $100 bonus (6 min ago)",
    "Emma from Australia passed FundingPips challenge (8 min ago)",
    "James from Germany launched AI agency (11 min ago)",
    "Lisa from Philippines unlocked $200/day autopilot (14 min ago)",
    "David from Nigeria just got $50k prop account (17 min ago)",
    "Sophia from Brazil started quantum dropshipping store (19 min ago)",
    "Ryan from India claimed Exness $1850 IB payout (22 min ago)",
    "Olivia from France joined the 2049 money matrix (25 min ago)"
]

# Scrolling ticker
ticker_text = " 🔥 " + " • ".join(ticker_messages) + " 🔥 "
st.markdown(f'<div class="ticker"><marquee>{ticker_text}</marquee></div>', unsafe_allow_html=True)

st.markdown("<h1 class='big-title'>Find Your Perfect 2049 Money Path</h1>", unsafe_allow_html=True)
st.markdown("<p style='text-align:center;font-size:1.4rem'>9 quick questions → the #1 job that will make you $10k–$1M+/month in 2025</p>", unsafe_allow_html=True)

# Timer
placeholder = st.empty()
timer_seconds = 24 * 3600 - 1  # 23:59:59
while timer_seconds > 0:
    h, m, s = timer_seconds // 3600, (timer_seconds % 3600) // 60, timer_seconds % 60
    placeholder.markdown(f'<div class="timer">⚠️ Quiz Closes in {h:02d}:{m:02d}:{s:02d}</div>', unsafe_allow_html=True)
    time.sleep(1)
    timer_seconds -= 1

# Initialize session state
if 'step' not in st.session_state:
    st.session_state.step = 1
    st.session_state.answers = {}
    st.session_state.skills = []

# Quiz logic (same as HTML version)
def next_step(step, value=None):
    if value:
        st.session_state.answers[step] = value
    st.session_state.step += 1

# Questions
if st.session_state.step == 1:
    st.markdown("### 1. How much do you want to earn per month?")
    if st.button("💰 $1k–$10k", key="q1a"): next_step(1, "10k")
    if st.button("💎 $10k–$50k", key="q1b"): next_step(1, "50k")
    if st.button("🚀 $50k–$1M+", key="q1c"): next_step(1, "1M")

elif st.session_state.step == 9:
    st.markdown("### Your Perfect 2049 Job Is...")
    # Same result logic as HTML
    result_text = "Daily tasks & surveys – perfect for beginners!"
    result_link = "https://www.ysense.com/?rb=221792458"
    
    if st.session_state.answers.get(1) in ["50k", "1M"] and "trading" in st.session_state.skills:
        result_text = "Funded Trader 2049 – Get $100k–$1M account!"
        result_link = "YOUR_FUNDINGPIPS_LINK"
    
    st.markdown(f"<h2 style='color:#00ffea'>{result_text}</h2>", unsafe_allow_html=True)
    st.markdown(f"[⚡ START NOW – CLAIM $500 BONUS]({result_link})")

else:
    st.write(f"Question {st.session_state.step} coming soon... (full version has all 9 questions)")

st.markdown("---")
st.markdown("👥 **87,492+ people took this quiz this week**")o
