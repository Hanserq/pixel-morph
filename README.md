# Pixel Morph — Reversible Pixel Repositioning Tool  
_Offline, deterministic, password-protected visual remapping._

---

## 📌 What is Pixel Morph?

**Pixel Morph** is a reversible image–transformation tool that takes **two images**:

- **Source** → supplies **colors**
- **Target** → supplies **structure / layout**

It then **repositions** every RGB pixel of the source image into a new image that resembles the target.  
Unlike filters or blends, the source pixels are **never altered**—they are only **moved**.

This mapping is then optionally **encrypted** and embedded inside a PNG for safe, lossless transport.  
Anyone with the password can reconstruct the original image perfectly.

---

## 🎯 Why does this exist?

Modern messaging apps often compress or modify images.  
Pixel Morph was built as a **camouflage + reversible transformation system** for cases where:

- You want to **hide an image in plain sight** while sending it.
- You need transformation that remains **100% reversible**.
- You want **offline, client-side only** encryption.
- You want a camo image that looks like a **normal PNG**, while secretly carrying encrypted payload.

This technique is inspired by your **Blackout Project**, but uses a different approach based on **pixel permutation instead of encryption-within-pixels**.

---

## 🔧 How it works (short technical overview)

1. Both images are resized/fit to the same working canvas.
2. The **target image** is analyzed using one of two ordering modes:
   - **Tone mode** → orders pixels by brightness + edges.
   - **Mask mode** → orders by thresholded binary shapes.
3. The source image’s pixels are mapped to the sorted positions from the target.
4. This creates a **morphed image** with:
   - The **colors** of the source
   - The **layout / tonality** of the target
5. A complete pixel-mapping table is generated.
6. When encoding:
   - The mapping is **AES-GCM encrypted** using PBKDF2
   - The ciphertext is stored inside a custom PNG chunk (`rNdX`).
7. When decoding:
   - The camo PNG is read
   - The payload is decrypted using the password
   - The original image is reconstructed exactly

No data loss. No compression artifacts. No cloud server. No tracking.

---

## 🧪 What can you use it for?

✅ **Secure reversible transformations**  
Send images disguised as normal aesthetic compositions.

✅ **Offline image protection**  
Everything runs locally in the browser—nothing leaves your device.

✅ **Camo messages**  
Hide the real content in a harmless-looking picture.

✅ **Art / stylization experiments**  
Blend structure of any image with colors of another, like:
- Face outlines mapped to landscape colors  
- City skyline mapped to sunset colors  
- Portrait silhouettes structured using other shapes  

✅ **Steganography-adjacent workflows**  
Not classic steganography, but functionally similar with far higher capacity:  
Every pixel participates in a reversible permutation.

✅ **Educational uses**  
Perfect for teaching:
- AES-GCM encryption  
- PBKDF2 key derivation  
- PNG chunk manipulation  
- Pixel-based ordering algorithms (Morton codes, tone mapping)  

---

## 🖼️ Screenshots / Examples

> Replace the placeholders with your actual tool screenshots.

### **Example 1 — Basic Morph Preview**
_(Insert Screenshot #1 here)_  
This shows the interface with Source, Target, and the generated Preview.  
You can see how colors from the source flow into the structure of the target.

---

### **Example 2 — Encrypted Camo PNG Output**
_(Insert Screenshot #2 here)_  
This image is what you send to someone.  
It looks normal, but secretly contains a fully encrypted permutation mapping.

---

### **Example 3 — Instant Recovery**
_(Insert Screenshot #3 here)_  
Enter the password → preview or download the recovered original image exactly.

---

## 🚀 Features

- ✅ Reversible pixel remapping  
- ✅ AES-GCM encryption  
- ✅ PBKDF2-SHA256 with selectable parameters  
- ✅ PNG chunk embedding  
- ✅ Preview & Decode  
- ✅ Swap Source/Target roles  
- ✅ Fit modes (Contain, Cover, Stretch)  
- ✅ Analyzer for recommended size based on payload limits  
- ✅ Auto-preview  
- ✅ File-safe (no compression, no EXIF issues)  
- ✅ Offline & open-source  
- ✅ Keyboard shortcuts (X = Swap, H = Help, P = Preview, E = Encode)

---

## 🧭 Quick Usage Guide

### **1. Load Source + Target**
- Source → provides **color**
- Target → provides **layout**

### **2. Click Preview**
See how the morph will look.

### **3. Encode to PNG**
- Set a password
- Click **Encode & Download**
- You get a normal-looking PNG with encrypted mapping inside

### **4. Decode**
- Pick the camo PNG
- Enter the password
- Click **Preview Decode**
- Download recovered PNG

---

## ✅ Supported Browsers

- ✅ Chrome  
- ✅ Edge  
- ✅ Brave  
- ✅ Safari (Desktop & iOS)  
- ✅ Firefox (with minor rendering differences)

---

## 📄 License

MIT License — free to use, modify, and distribute.

---

## ⭐ If you like this project...

Leave a star ⭐ on GitHub! It motivates further development & enhancements.

