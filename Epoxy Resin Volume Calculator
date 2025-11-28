import streamlit as st
import math

# --- CONFIGURATION ---
st.set_page_config(
    page_title="Epoxy Resin Calculator | River Tables & Art",
    page_icon="💧",
    layout="centered"
)

# --- STYLING ---
st.markdown("""
<style>
    .big-metric { font-size: 32px !important; font-weight: bold; color: #2196F3; }
    .money-box { background-color: #e3f2fd; padding: 20px; border-radius: 10px; border: 1px solid #90caf9; }
</style>
""", unsafe_allow_html=True)

# --- HEADER ---
st.title("💧 Epoxy Resin Calculator")
st.markdown("Don't waste expensive resin. Calculate exactly how much you need for your pour.")
st.divider()

# --- INPUTS ---
st.subheader("1. Measure Your Mold")
shape = st.selectbox("Shape", ["Rectangle (Table/Tray)", "Circle (Coaster/Art)"])

col1, col2 = st.columns(2)

if shape == "Rectangle (Table/Tray)":
    with col1:
        length = st.number_input("Length (inches)", value=24.0)
        width = st.number_input("Width (inches)", value=12.0)
    with col2:
        depth = st.number_input("Depth/Thickness (inches)", value=1.0)
    
    # Math: L * W * H = Cubic Inches
    volume_cubic_inches = length * width * depth

else: # Circle
    with col1:
        diameter = st.number_input("Diameter (inches)", value=4.0)
    with col2:
        depth = st.number_input("Depth/Thickness (inches)", value=0.5)
    
    # Math: pi * r^2 * h
    radius = diameter / 2
    volume_cubic_inches = math.pi * (radius ** 2) * depth

# --- CALCULATIONS ---
# Conversion factors
# 1 cubic inch = 0.554 fluid ounces
# 1 gallon = 231 cubic inches
total_oz = volume_cubic_inches * 0.554113
total_liters = total_oz * 0.0295735
total_gallons = volume_cubic_inches / 231

# Safety Margin (Always add 5-10% for spills/mixing cups)
safe_oz = total_oz * 1.05

# --- RESULTS ---
st.divider()
st.subheader("🧪 Total Mix Needed (Resin + Hardener)")

c1, c2 = st.columns(2)
c1.markdown(f"""
<div class="money-box">
    <div style="font-size:14px">Fluid Ounces</div>
    <div class="big-metric">{safe_oz:.1f} fl oz</div>
    <div style="font-size:12px; color: #666;">(Includes 5% safety margin)</div>
</div>
""", unsafe_allow_html=True)

c2.markdown(f"""
<div class="money-box">
    <div style="font-size:14px">Liters</div>
    <div class="big-metric">{total_liters * 1.05:.2f} L</div>
</div>
""", unsafe_allow_html=True)

st.write("")
st.info(f"📝 **Mixing Note:** Most resins are 1:1 ratio. You need **{safe_oz/2:.1f} oz** of Part A and **{safe_oz/2:.1f} oz** of Part B.")

# --- MONETIZATION (The High Ticket Items) ---
st.divider()
st.subheader("🛍️ Get the Right Resin")

# Logic to recommend the right TYPE of resin (Deep pour vs Coating)
if depth > 1.0:
    st.warning("⚠️ **Deep Pour Alert:** You are pouring over 1 inch thick. You MUST use 'Deep Pour' resin or it will overheat and crack.")
    st.link_button("👉 Buy Promise Deep Pour Resin (Best Seller)", "https://amzn.to/4im5zpe") 
else:
    st.write("For thin coats and coasters, use a standard Table Top resin.")
    st.link_button("👉 Buy Promise Table Top Epoxy", "https://amzn.to/4ox0oo8")

# Upsell Tools
with st.expander("Don't forget mixing tools"):
    st.write("You will need graduated cups and stir sticks.")
    st.link_button("👉 Get Mixing Kit ($15)", "https://amzn.to/44gz9a7")
