# Testing and QA

- **Say "fixed" only after seeing it live yourself.** Why: claimed fixes weren't there four times. (bannquet, Abis, jasiahpowers, logiparty)
- **After a data-shape change, load every page that reads that data.** Why: a bannquet change broke every trip page. (bannquet)
- **Check phone widths before merge: no sideways scroll or dead space.** Use WebKit iPhone emulation for iPhone-only bugs. (drewdella, favoritesonnyc)
- **Test 3D, WebGL and fonts on real devices.** Agent browsers have no GPU or Apple fonts, so GPU glitches need Jake's device. 3D upgrades get checked by eye. (metrotapes)
- **Use one standing test account, on the preview database only.** Delete test data right away, and know what's shared with live. Why: Jake found leftover test posts. (bannquet)
- **Before a test form submission, check where it actually sends.** Why: a CMS setting sent a test to the client. (jasiahpowers)

## How to decide how much to test
- **Match the check to the risk** (see [git.md](git.md)). Jake checks low-risk copy and style tweaks live. Changes to data, auth, forms, payments, routing or a client-visible redesign get a real check on the preview, on every page touched, on desktop and phone.
