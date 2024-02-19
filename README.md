# Pantau Pemilu 2024 Dump

This repository contains the data from the
[pemilu2024.kpu.go.id](https://pemilu2024.kpu.go.id) website. The data is in
JSON format, so you can track changes over time with `git diff`.

Read the the data documentation
[data-pemilu.vercel.app](https://data-pemilu.vercel.app/).

```typescript copy
type SaveFile = {
  data: unknown;
  url: string;
};

const saveFile = async ({ data, url }: SaveFile) => {
  const isValidUrl = url.startsWith("https://sirekap-obj-data.kpu.go.id");

  if (!isValidUrl) {
    throw new Error("Invalid url");
  }

  const fileName = url.replace("https://sirekap-obj-data.kpu.go.id", "");

  Bun.write(`dump/${fileName}`, JSON.stringify(data, null, 2), {
    createPath: true,
  });
};
```
