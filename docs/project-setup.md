---
id: project-setup
title: crypto dashboard guide
---

# Crypto Dashboard - Setup Guide 🚀

## 1️⃣ **Web App Setup (Next.js)**

To run the Next.js app, follow these steps:

```bash
git clone https://github.com/faisalit86/web-app
cd web-app
npm install
npm run dev

API Integration (React Query)

We use the CoinGecko API to fetch cryptocurrency prices.

The API call is handled using React Query for caching and auto-refetching.

Fetching Data (React Query)
import { useQuery } from "@tanstack/react-query";

async function fetchCryptoPrices() {
  const res = await fetch("https://api.coingecko.com/api/v3/simple/price?ids=bitcoin,ethereum&vs_currencies=usd");
  return res.json();
}

export default function CryptoPrices() {
  const { data, isFetching } = useQuery({
    queryKey: ["cryptoPrices"],
    queryFn: fetchCryptoPrices,
  });

  return isFetching ? <p>Loading...</p> : <pre>{JSON.stringify(data, null, 2)}</pre>;
}


React Query handles API caching and automatic refetching.

State Management (Zustand + React Query)

Zustand manages search filtering.

State Management Setup (Zustand)

import { create } from "zustand";

const useSearchStore = create((set) => ({
  searchQuery: "",
  setSearchQuery: (query) => set({ searchQuery: query }),
}));

export default useSearchStore;




Challenges & Solutions
```
