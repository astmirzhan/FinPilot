# FinPilot

Android portfolio tracker. Add your assets, set your risk profile and get an analysis of risk, diversification and allocation with plain-language recommendations. Everything is stored on the device.

## Features

- **Portfolio:** add assets with a name, category, amount and risk level (1 to 10 on a slider), see the list and the total value.
- **Categories:** Stocks, ETF, Bonds, Crypto, Cash, Real Estate, Gold, Commodities, Other.
- **Risk profile:** Conservative, Balanced or Aggressive.
- **Analysis:** total value, allocation by category (with a custom-drawn chart), a weighted risk score, a diversification score and generated recommendations based on your profile.
- **Local storage:** assets and the risk profile are saved in the app's private `SharedPreferences` as JSON. No account, no network.

## How the analysis works

`PortfolioAnalyzer` (in `domain/`) works on a list of assets:

- **Allocation:** share of each category in the total value, in percent.
- **Risk score:** the asset risk levels weighted by their share of the portfolio.
- **Diversification score:** based on how concentrated the allocation is across categories (a Herfindahl-style concentration, normalised by the number of categories).
- **Recommendations:** rules that look at crypto, cash, ETF and bond shares, the largest category and the chosen risk profile.

## Project structure

```
app/src/main/java/com/astmirzhan/finpilot/
├── MainActivity.kt, PortfolioActivity.kt, AddAssetActivity.kt,
│   RiskProfileActivity.kt, AnalysisActivity.kt   screens
├── model/      Asset, AssetCategory, RiskProfile
├── data/       PortfolioRepository (SharedPreferences + JSON)
├── domain/     PortfolioAnalyzer
├── ui/         AssetAdapter
└── view/       PortfolioChartView (custom view)
```

## Build

- Kotlin, Android Views, Material Components
- `minSdk` 24, `targetSdk` 36
- Open the project in Android Studio and run the `app` configuration, or `./gradlew assembleDebug`.

## Status

University project and learning exercise. It is not financial advice: the recommendations are simple rules, not investment guidance.

## License

[MIT](LICENSE)
