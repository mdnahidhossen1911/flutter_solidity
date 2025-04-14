# 📱🛡️ Flutter + Solidity Project (Bangla Guide)

এটি একটি Flutter + Solidity ভিত্তিক প্রজেক্ট যেখানে আপনি মোবাইল অ্যাপ থেকে ব্লকচেইন কন্ট্রাক্টের সাথে যোগাযোগ করতে পারবেন। এই README আপনাকে ডেভেলপমেন্টের সঠিক নিয়ম, স্টাইল, এবং নিরাপত্তা সম্পর্কিত নির্দেশনা দিবে।

---

## 📦 টেক স্ট্যাক

| টেকনোলজি | বিবরণ |
|----------|--------|
| Flutter  | Frontend মোবাইল অ্যাপ |
| Web3dart | Flutter এর মাধ্যমে Ethereum RPC কল |
| Solidity | Ethereum Smart Contract |
| Hardhat/Remix | Smart Contract ডেভেলপ ও টেস্টিং টুল |
| Ganache/Testnet | লোকাল বা অনুশীলন নেটওয়ার্ক |

---

## 🚀 প্রজেক্ট স্ট্রাকচার

```
lib/
├── main.dart
├── screens/
│   └── home_screen.dart
├── services/
│   └── web3_service.dart
contracts/
└── MyContract.sol
README.md
pubspec.yaml
```

---

## 🔗 Solidity Integration Flow (ধাপ ভিত্তিক)

1. **Smart Contract লিখুন (Solidity)**
2. **Hardhat দিয়ে Compile ও Deploy করুন**
3. **ABI ও Contract Address Flutter-এ ইম্পোর্ট করুন**
4. **Web3dart ব্যবহার করে Function Call করুন**
5. **Result UI-তে দেখান**

---

## ✅ Solidity ডেভেলপমেন্ট নিয়মাবলী

- `require()` দিয়ে ইনপুট ভ্যালিডেশন করুন
- `event` ব্যবহার করে লগিং করুন
- প্রতিটি `function`-এ visibility (public/private) নির্ধারণ করুন
- Reentrancy থেকে বাঁচতে state আগে আপডেট করুন, তারপর transfer
- Compiler version নির্দিষ্ট করুন:
  ```solidity
  pragma solidity ^0.8.20;
  ```

### 🛡️ নিরাপত্তা রুলস

- `reentrancy guard` ব্যবহার করুন
- `fallback()` ও `receive()` function সঠিকভাবে আলাদা করুন
- সর্বদা ইনপুট validate করুন
- বড় ট্রানজাকশনের জন্য `gas limit` নির্ধারণ করুন

---

## 🎨 Flutter কোডিং স্টাইল গাইডলাইন (Bangla)

### ফোল্ডার গঠন:

- `screens/` → UI
- `services/` → Web3/HTTP ইত্যাদি
- `models/` → ডাটা মডেল
- `widgets/` → Reusable UI components

### কোডিং নিয়ম:

- সব ক্লাস নাম **PascalCase**: `HomeScreen`, `Web3Service`
- ভেরিয়েবল নাম **camelCase**: `contractAddress`, `web3client`
- UI কোডে context না পাঠিয়ে Provider বা Controller ব্যবহার করুন
- Bloc বা Provider দিয়ে state পরিচালনা করুন

---

## 🔌 Web3dart দিয়ে Smart Contract কল:

```dart
final contract = DeployedContract(
  ContractAbi.fromJson(abiCode, "MyContract"),
  EthereumAddress.fromHex(contractAddress),
);

final function = contract.function('getValue');
final result = await client.call(
  contract: contract,
  function: function,
  params: [],
);
```

---

## 🧪 টেস্টিং

- Solidity কন্ট্রাক্ট → Hardhat Test (Chai, Mocha)
- Flutter App → Widget Test, Integration Test

---

## 🌐 ডিপ্লয়মেন্ট

1. Smart Contract → Remix/Hardhat দিয়ে testnet/mainnet-এ ডিপ্লয় করুন
2. Flutter App → Play Store / App Store
3. .env ফাইলে contract address ও RPC url রাখুন

---

## 📘 ভবিষ্যত পরিকল্পনা

- Wallet Connect সাপোর্ট
- NFT Minting ফিচার
- Real-time Blockchain Event Subscription

---

## ✍️ শেষ কথা

এই ডকুমেন্ট আপনার Solidity ও Flutter ভিত্তিক ড্যাপ (DApp) তৈরি করার পথকে সুগম করবে। সঠিক নিয়ম মেনে কাজ করলে ডেভেলপমেন্ট নিরাপদ ও maintainable হবে।
