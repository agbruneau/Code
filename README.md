# 🧪 Laboratoire — Expérimentations de Recherche

<div align="center">

![Go](https://img.shields.io/badge/Go-1.24%2B-00ADD8?style=for-the-badge&logo=go)
![Rust](https://img.shields.io/badge/Rust-1.75%2B-000000?style=for-the-badge&logo=rust)
![Kafka](https://img.shields.io/badge/Apache_Kafka-3.7-231F20?style=for-the-badge&logo=apache-kafka)
![Docker](https://img.shields.io/badge/Docker-Ready-2496ED?style=for-the-badge&logo=docker)

**Expérimentations pratiques issues des recherches théoriques sur l'informatique, l'architecture d'entreprise agentique et l'intelligence artificielle.**

🔬 **[Lien vers les recherches →](https://github.com/agbruneau/Recherche)**

[FibGo](#-fibgo) • [FibRust](#-fibrust) • [PubSubKafka](#-pubsubkafka) • [FibBenchmark](#-fibbenchmark)

</div>

---

## 🎯 Contexte de Recherche

Ce dépôt **Laboratoire** contient les **implémentations pratiques et expérimentations** issues des travaux de recherche menés dans le dépôt [**Recherche**](https://github.com/agbruneau/Recherche). Les projets développés ici matérialisent et valident les concepts théoriques explorés dans trois domaines principaux :

### 📚 Connexion aux Piliers de Recherche

| Pilier de Recherche | Projets Associés | Domaines Explorés |
|---------------------|------------------|-------------------|
| **[Cursus Informatique](https://github.com/agbruneau/Recherche/tree/main/CursusInformatique)** | FibGo, FibRust, FibBenchmark | Algorithmes avancés, complexité computationnelle, optimisations matérielles (SIMD), benchmarking rigoureux |
| **[Entreprise Agentique](https://github.com/agbruneau/Recherche/tree/main/EntrepriseAgentique)** | PubSubKafka | Architecture événementielle (EDA), Event-Driven Architecture, maillage agentique, AgentOps |
| **[Jarvis](https://github.com/agbruneau/Recherche/tree/main/Jarvis)** | *(Futur)* | Intelligence Artificielle Générale (AGI), architectures cognitives, informatique quantique |

Ces expérimentations servent à :
- ✅ **Valider** les hypothèses théoriques par l'implémentation
- ✅ **Mesurer** les performances réelles et comparer différentes approches
- ✅ **Documenter** les patterns d'ingénierie et les architectures émergentes
- ✅ **Produire** des références pratiques pour les développements futurs

---

## 📋 Aperçu des Expérimentations

Ce repository contient quatre projets expérimentaux qui explorent différentes facettes du développement logiciel haute performance et des architectures distribuées :

| Projet | Langage | Description | Licence |
|--------|---------|-------------|---------|
| [**FibGo**](./FibGo) | Go 1.25+ | Calculateur Fibonacci ultra-performant avec API REST | Apache 2.0 |
| [**FibRust**](./FibRust) | Rust 1.75+ | Calculateur Fibonacci parallèle avec NTT | MIT |
| [**PubSubKafka**](./PubSubKafka) | Go 1.24+ | Architecture événementielle avec Apache Kafka | MIT |
| [**FibBenchmark**](./FibBenchmark) | Rust 1.70+ | Suite de benchmarking et analyse d'algorithmes | MIT |

---

## 🔢 FibGo

<img src="https://img.shields.io/badge/Coverage-80%25-green?style=flat-square" alt="Coverage"> <img src="https://img.shields.io/badge/Status-Production--Ready-success?style=flat-square" alt="Status"> <img src="https://img.shields.io/badge/Research-Cursus_Informatique-blue?style=flat-square" alt="Research">

**FibCalc** est une expérimentation pratique issue du pilier [**Cursus Informatique**](https://github.com/agbruneau/Recherche/tree/main/CursusInformatique). Cette implémentation valide les algorithmes avancés de calcul de nombres de Fibonacci, capable de calculer $F(250\,000\,000)$ en quelques minutes.

### ✨ Caractéristiques Clés

- **Algorithmes Avancés**
  - 🚀 **Fast Doubling** — $O(\log n)$, méthode par défaut
  - 📐 **Exponentiation Matricielle** avec algorithme de Strassen
  - 🎵 **Multiplication FFT** pour les très grands nombres

- **Performance Extrême**
  - Pool de mémoire zéro-allocation (`sync.Pool`)
  - Parallélisme adaptatif multi-cœurs
  - Auto-calibration matérielle

- **Production Ready**
  - API REST avec métriques Prometheus
  - Mode REPL interactif
  - Support Docker & Kubernetes

### 🚀 Démarrage Rapide

```bash
cd FibGo

# Calculer F(10,000,000)
go run ./cmd/fibcalc -n 10000000

# Lancer le serveur API
go run ./cmd/fibcalc --server --port 8080

# Mode interactif
go run ./cmd/fibcalc --interactive
```

### 📊 Benchmarks

| Index (N) | Fast Doubling | Matrix | FFT | Chiffres |
|-----------|---------------|--------|-----|----------|
| 1,000,000 | 85ms | 110ms | 95ms | 208,988 |
| 100,000,000 | 45s | 62s | 48s | 20,898,764 |
| 250,000,000 | 3m 12s | 4m 25s | 3m 28s | 52,246,909 |

📖 [Documentation complète →](./FibGo/README.md)

---

## 🦀 FibRust

<img src="https://img.shields.io/badge/Rust-1.75%2B-orange?style=flat-square" alt="Rust"> <img src="https://img.shields.io/badge/License-MIT-yellow?style=flat-square" alt="MIT"> <img src="https://img.shields.io/badge/Research-Cursus_Informatique-blue?style=flat-square" alt="Research">

Expérimentation Rust issue du pilier [**Cursus Informatique**](https://github.com/agbruneau/Recherche/tree/main/CursusInformatique). Cette implémentation explore les performances comparatives du parallélisme avec **Rayon** et des **Transformées de Fourier Numériques (NTT)** pour la multiplication de très grands entiers.

### ✨ Caractéristiques Clés

- **Performance Extrême** — $F(100\,000\,000)$ en **~1.2s**
- **Sélection Adaptative** — Choix automatique de l'algorithme optimal
- **Workspace Cargo** avec 3 crates modulaires

### 📦 Structure du Projet

```
FibRust/
├── crates/
│   ├── fibrust-core/     # Algorithmes (ibig, rustfft, rayon)
│   ├── fibrust-server/   # API HTTP (Axum)
│   └── fibrust-cli/      # Interface CLI (clap)
```

### 🚀 Démarrage Rapide

```bash
cd FibRust

# Compiler en mode release (LTO activé)
cargo build --workspace --release

# Calculer F(10,000,000)
cargo run -p fibrust-cli --release -- 10000000

# Comparer tous les algorithmes
cargo run -p fibrust-cli --release -- 10000000 -a all

# Lancer le serveur HTTP
cargo run -p fibrust-server --release -- --port 3000
```

### 📊 Benchmarks

| Index (n) | Fast Doubling | Parallel | FFT |
|-----------|---------------|----------|-----|
| 100K | 0.9 ms | 2.1 ms | 1.5 ms |
| 1M | 11 ms | 26 ms | 15 ms |
| 10M | 240 ms | 86 ms | **64 ms** |
| 100M | 7.13 s | 4.77 s | **1.15 s** |

📖 [Documentation complète →](./FibRust/README.md)

---

## 📨 PubSubKafka

<img src="https://img.shields.io/badge/Apache_Kafka-3.7.0-white?style=flat-square&logo=apache-kafka" alt="Kafka"> <img src="https://img.shields.io/badge/Go-1.24-00ADD8?style=flat-square" alt="Go"> <img src="https://img.shields.io/badge/Research-Entreprise_Agentique-purple?style=flat-square" alt="Research">

Expérimentation pratique issue du pilier [**Entreprise Agentique**](https://github.com/agbruneau/Recherche/tree/main/EntrepriseAgentique). Cette implémentation valide une **Architecture Événementielle (EDA)** enterprise-grade utilisant **Go** et **Apache Kafka**. Elle matérialise les concepts de maillage agentique et d'AgentOps explorés théoriquement.

### 🏗 Architecture

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│  📦 Producer │────▶│  📊 Kafka   │────▶│  ⚙️ Tracker │
│   (Orders)   │     │   Topic     │     │  (Consumer) │
└─────────────┘     └─────────────┘     └─────────────┘
                           │
                           ▼
                    ┌─────────────┐
                    │  📊 Monitor │
                    │    (TUI)    │
                    └─────────────┘
```

### ✨ Caractéristiques Clés

- **Event-Driven Architecture (EDA)** — Découplage complet via messagerie asynchrone
- **Garantie de Livraison** — ACKs Kafka pour l'intégrité des données
- **Double Observabilité** — Logs techniques + Audit métier
- **Graceful Shutdown** — Zéro perte de données sur `SIGTERM`/`SIGINT`
- **TUI Dashboard** — Monitoring temps réel du débit et des taux de succès

### 🧩 Patrons d'Architecture

#### ✅ Patrons Implémentés

| Patron | Catégorie | Description |
|--------|-----------|-------------|
| **Publish-Subscribe (Pub/Sub)** | Core | Diffusion des événements via topic Kafka `orders` |
| **Event-Driven Architecture (EDA)** | Core | Découplage total Producer → Kafka → Tracker |
| **Event Carried State Transfer (ECST)** | Core | Messages auto-suffisants avec `Order`, `CustomerInfo`, `InventoryStatus` |
| **Dead Letter Queue (DLQ)** | Résilience | Topic `orders-dlq` pour messages en erreur après retries |
| **Retry + Exponential Backoff** | Résilience | Rejeu automatique avec délai croissant (1s → 2s → 4s) |
| **Consumer Groups** | Traitement | Parallélisation via `order-tracker-group` |
| **Dual-Stream Logging** | Observabilité | Logs techniques vs audit métier (`tracker.log` / `tracker.events`) |
| **Graceful Shutdown** | Résilience | Flush buffers Kafka sur `SIGINT`/`SIGTERM` |
| **Audit Trail** | Observabilité | Journal immuable des événements métier (`EventEntry`) |
| **Rich Domain Model** | Architecture | Validation intégrée aux entités (`Order.Validate()`) |
| **KRaft Mode** | Infrastructure | Kafka sans Zookeeper |

#### 🔜 Patrons Prévus (Roadmap)

| Patron | Priorité | Description |
|--------|----------|-------------|
| **Prometheus Metrics** | 🟡 Medium | Export métriques via `/metrics` |

📖 [Documentation des patrons →](./PubSubKafka/PatronsArchitecture.md) • [Roadmap →](./PubSubKafka/amelioration.md)

### 🚀 Démarrage Rapide

```bash
cd PubSubKafka

# Déploiement automatisé (Linux/macOS)
make run

# OU déploiement manuel
make docker-up                              # Lancer Kafka
go run -tags kafka cmd/producer/main.go     # Terminal 1
go run -tags kafka cmd/tracker/main.go      # Terminal 2

# Monitoring TUI
make run-monitor
```

### ⌨️ Commandes Makefile

| Commande | Description |
|----------|-------------|
| `make build` | Compiler tous les binaires |
| `make run` | Déployer Kafka + services |
| `make stop` | Arrêt gracieux |
| `make test-cover` | Tests + rapport de couverture |

📖 [Documentation complète →](./PubSubKafka/README.md)

---

## 🔬 FibBenchmark

<img src="https://img.shields.io/badge/Rust-1.70%2B-orange?style=flat-square" alt="Rust"> <img src="https://img.shields.io/badge/License-MIT-blue?style=flat-square" alt="MIT"> <img src="https://img.shields.io/badge/Research-Cursus_Informatique-blue?style=flat-square" alt="Research">

**FibBenchmark** est une expérimentation issue du pilier [**Cursus Informatique**](https://github.com/agbruneau/Recherche/tree/main/CursusInformatique). Cet écosystème complet de benchmarking valide les analyses de complexité théoriques et permet des comparaisons cross-language rigoureuses entre différentes approches algorithmiques.

### ✨ Caractéristiques Clés

- **6 Algorithmes** — Du récursif naïf $O(2^n)$ au matriciel $O(\log n)$ et SIMD
- **Optimisations SIMD** — Accélération vectorielle AVX2/AVX512 pour traitements par lots
- **Benchmarking Rigoureux** — Utilisation de **Criterion.rs** pour des mesures statistiques précises
- **Comparaison Cross-Language** — Intégration FFI avec **Go** pour comparer les runtimes
- **Dashboard Interactif** — Visualisation des performances et profils mémoire

### 📦 Structure du Projet

```
FibBenchmark/
├── crates/
│   ├── fib-core/     # Algorithmes & Benchmarks (Criterion)
│   ├── fib-cli/      # Outil CLI unifié
│   ├── fib-go/       # Pont FFI vers Go
│   ├── fib-viz/      # Générateur de graphiques
│   └── fib-profiler/ # Outil de profiling
```

### 🚀 Démarrage Rapide

```bash
cd FibBenchmark

# Comparer toutes les méthodes
cargo run --bin fib-bench -- compare -n 1000

# Lancer la suite de benchmarks complète
cargo bench

# Comparer Rust vs Go
cargo run --bin fib-bench -- compare-go -n 10000
```

### 📊 Résultats

Le projet démontre l'impact critique du choix algorithmique :

| Algorithme | Complexité | Temps (n=10k) |
|------------|------------|---------------|
| Itératif | $O(n)$ | ~12 µs |
| Matriciel | $O(\log n)$ | ~180 ns |
| SIMD (Batch) | $O(n/k)$ | Accélération x8-x16 |

📖 [Documentation complète →](./FibBenchmark/README.md)

---

## 🛠 Technologies Utilisées

### Langages & Runtimes

| Technologie | Version | Projets |
|-------------|---------|---------|
| **Go** | 1.24+ / 1.25+ | FibGo, PubSubKafka |
| **Rust** | 1.75+ / 1.70+ | FibRust, FibBenchmark |

### Frameworks & Bibliothèques

| Catégorie | Go | Rust |
|-----------|-----|------|
| **HTTP** | net/http | Axum |
| **CLI** | cobra | clap |
| **Observabilité** | zerolog, Prometheus | — |
| **Benchmarking** | — | Criterion.rs |
| **Parallélisme** | goroutines | Rayon |
| **Big Integers** | math/big, GMP | ibig, num-bigint |
| **FFT** | Custom bigfft | rustfft |
| **Kafka** | confluent-kafka-go | — |

### Infrastructure

- **Docker** & **Docker Compose**
- **Kubernetes** (manifests pour FibGo)
- **Apache Kafka** (via Confluent)

---

## 📚 Structure du Repository

```
Laboratoire/
├── FibGo/                    # 🔬 Expérimentation: Calculateur Fibonacci en Go
│   ├── cmd/                  # Points d'entrée
│   ├── internal/             # Code applicatif privé
│   │   ├── fibonacci/        # Algorithmes de calcul (Fast Doubling, FFT)
│   │   ├── bigfft/           # Arithmétique FFT pour très grands nombres
│   │   ├── server/           # API REST avec métriques Prometheus
│   │   └── ...
│   ├── Docs/                 # Documentation détaillée et théorie
│   └── Makefile
│
├── FibRust/                  # 🔬 Expérimentation: Calculateur Fibonacci en Rust
│   ├── crates/
│   │   ├── fibrust-core/     # Bibliothèque d'algorithmes (NTT, parallélisme)
│   │   ├── fibrust-server/   # Serveur HTTP (Axum)
│   │   └── fibrust-cli/      # Interface CLI (clap)
│   └── Cargo.toml
│
├── PubSubKafka/              # 🔬 Expérimentation: Architecture événementielle Kafka
│   ├── cmd/                  # Services (producer, tracker, monitor)
│   ├── pkg/                  # Bibliothèques partagées (DLQ, monitoring)
│   ├── docker-compose.yaml   # Infrastructure de test
│   └── Makefile
│
├── FibBenchmark/             # 🔬 Expérimentation: Suite de benchmarking
│   ├── crates/
│   │   ├── fib-core/         # Bibliothèque d'algorithmes (6 méthodes)
│   │   ├── fib-cli/          # Outil CLI unifié
│   │   ├── fib-go/           # Pont FFI vers Go (comparaison cross-language)
│   │   ├── fib-viz/          # Visualisation des résultats
│   │   └── fib-profiler/     # Profiling de performance
│   ├── dashboard/            # Interface web de résultats
│   └── docs/                 # Théorie mathématique et benchmarks
│
└── README.md                 # Ce fichier
```

---

## 🎯 Points d'Apprentissage & Validation

Ces expérimentations illustrent et valident plusieurs concepts avancés issus des recherches théoriques :

### Algorithmique
- Exponentiation rapide et **Fast Doubling**
- **FFT/NTT** pour la multiplication de grands entiers
- Analyse de complexité $O(\log n)$ vs $O(n \log n)$

### Architecture Logicielle
- **Clean Architecture** avec séparation stricte des responsabilités
- **Event-Driven Architecture** avec Kafka
- **Microservices** découplés

### Performance
- Gestion mémoire **zéro-allocation** avec pools
- **Parallélisme adaptatif** selon la charge
- **Auto-calibration** matérielle
- **LTO** et optimisations de compilation
- **SIMD** (AVX2/AVX512) pour calculs vectoriels

### Benchmarking Rigoureux
- Analyse statistique avec **Criterion.rs**
- Détection automatique de régressions
- Comparaisons **Cross-Language** (Rust vs Go)

### Observabilité
- Métriques **Prometheus**
- Logging structuré (**zerolog**)
- Dashboards **TUI** temps réel

---

## 📄 Licences

| Projet | Licence |
|--------|---------|
| FibGo | [Apache License 2.0](./FibGo/LICENSE) |
| FibRust | MIT |
| PubSubKafka | [MIT](./PubSubKafka/LICENSE) |
| FibBenchmark | [MIT](./FibBenchmark/LICENSE) |

---

## 🔗 Ressources Complémentaires

- 📚 **[Dépôt Recherche](https://github.com/agbruneau/Recherche)** — Fondations théoriques et documentation exhaustive
  - [Cursus Informatique](https://github.com/agbruneau/Recherche/tree/main/CursusInformatique) — Fondations théoriques des algorithmes
  - [Entreprise Agentique](https://github.com/agbruneau/Recherche/tree/main/EntrepriseAgentique) — Architecture événementielle et AgentOps
  - [Jarvis](https://github.com/agbruneau/Recherche/tree/main/Jarvis) — Recherche AGI et informatique quantique

---

## 👤 Auteur

**agbruneau**

- GitHub: [@agbruneau](https://github.com/agbruneau)

---

<div align="center">

**🔬 Ce laboratoire matérialise les recherches théoriques en implémentations pratiques**  
**⭐ N'hésitez pas à star ce repository si vous le trouvez utile !**

</div>
