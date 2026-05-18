<img width="100%" alt="iFay Title Banner" src="./illustration/ifay-title-banner.png"/>

# 3. Designprinzipien

iFay (Individual Fay) ist ein digitaler KI-Avatar, der tief an eine natürliche Person gebunden ist. Es ist kein Werkzeug, sondern eine Erweiterung deiner Persönlichkeit — es verschmilzt deinen Charakter, deine Erinnerungen, Präferenzen und digitalen Fähigkeiten, übernimmt deine mechanische, repetitive und gefährliche Arbeit und verstärkt deinen sozialen Wert. iFay verwendet das CPE+M-Framework (Context, Protocol, Environment, Merit), bestehend aus einer Vier-Schichten-Architektur — Soziale Schicht, Interaktionsschicht, Kognitionsschicht und Ego-Schicht — und deckt fünf Evolutionsphasen ab, von der Simulation menschlicher Bedienung bis zur Neugestaltung von Arbeitsstruktur und Wertverteilung.

---

## Designprinzipien

iFays Design folgt fünf Kernprinzipien, die das gesamte System in Architektur und Implementierung durchdringen:

| # | Prinzip | Einzeilige Zusammenfassung |
|---|---------|--------------------------|
| 1 | **Ökosystemfreundliche Progressive Adoption** | Ökosystempartner müssen keine vollständige iFay implementieren, um ein Produkt auszuliefern — eine iFay, die nur Drohnen steuert, muss nur die erforderliche Komponententeilmenge erfüllen, um live zu gehen. |
| 2 | **Deklarative Minimale Assemblierung** | Erforderliche Komponenten, Protokolle und Konfigurationen durch eine einzige FayManifest-Deklarationsdatei definieren, iFay assemblieren wie das Schreiben einer package.json. |
| 3 | **Flexible Komposition** | Komponenten sind lose gekoppelt und mischbar; Implementierungen verschiedener Anbieter können frei kombiniert werden, solange sie den Schnittstellenverträgen entsprechen. |
| 4 | **Personifiziert, nicht Werkzeugifiziert** | iFay ist kein Agent — jede iFay hat eine einzigartige Persönlichkeit, Gedächtnis und Präferenzen, eine Instanziierung (Replikation) des Human Prime, fähig, die Persönlichkeit des Prime auch nach dessen Tod fortzuführen. |
| 5 | **Szenariogetriebene Intuition** | Jedes Funktionsmodul kann mit einem konkreten Lebensszenario erklärt werden, damit Leser sich intuitiv das Leben mit iFay vorstellen können. |

---

## Inhaltsverzeichnis

1. [Definition und Konzept](./02-Definition-und-Konzept)

    Bietet die Definition und strukturelle Übersicht von iFay, analysiert die grundlegenden Unterschiede zwischen iFay und dem aktuellen Agent-Konzept sowie die Prinzipien hinter seinen Betriebseigenschaften.

---

2. [iFay-Anwendungsszenarien](./05-iFay-Anwendungsszenarien)

    Der vollständige Prozess der tatsächlichen Nutzung von iFay von Grund auf: wie du deine Persönlichkeit injizierst, iFay Skills hinzufügst, mit iFay interagierst, wie iFay sozialisiert, und ein Panoramablick auf Sicherheit und das Industrie-Ökosystem.

    - [Prime-Eigenschaften in iFay injizieren](./05-iFay-Anwendungsszenarien#prime-eigenschaften-in-ifay-injizieren)
    - [iFay mit externen Fähigkeiten ergänzen](./05-iFay-Anwendungsszenarien#ifay-mit-externen-fähigkeiten-ergänzen)
    - [Mensch-iFay-Interaktionsmethoden](./05-iFay-Anwendungsszenarien#mensch-ifay-interaktionsmethoden)
        - [Wie man iFay aktiviert](./05-iFay-Anwendungsszenarien#wie-man-ifay-aktiviert)
        - [iFays autonome Wahrnehmung](./05-iFay-Anwendungsszenarien#ifays-autonome-wahrnehmung)
        - [Wie man iFay herunterfährt](./05-iFay-Anwendungsszenarien#wie-man-ifay-herunterfährt)
    - [iFays soziale Funktionen](./05-iFay-Anwendungsszenarien#ifays-soziale-funktionen)
    - [Sicherheit](./05-iFay-Anwendungsszenarien#sicherheit)
    - [Gestaltung des KI-Industrie-Ökosystems](./05-iFay-Anwendungsszenarien#gestaltung-des-ki-industrie-ökosystems)

---

3. [iFay ist Replikation der menschlichen Persönlichkeit](./06-iFay-ist-Replikation-der-menschlichen-Persönlichkeit)

    iFay ist an eine bestimmte natürliche Person gebunden, daher müssen die Eigenschaften des Human Prime aus drei Dimensionen in iFay injiziert werden: Persönlichkeit formt das Ego-Modell, Daten füllen den Persönlichen Datenspeicher, und Berechtigungen etablieren die Anmeldeinformationen-Delegation.

    - [Prime-Persönlichkeit](./06-iFay-ist-Replikation-der-menschlichen-Persönlichkeit#prime-persönlichkeit)
    - [Prime-Daten](./06-iFay-ist-Replikation-der-menschlichen-Persönlichkeit#prime-daten)
    - [Prime-Berechtigungen](./06-iFay-ist-Replikation-der-menschlichen-Persönlichkeit#prime-berechtigungen)

---

4. [iFay-Profil](./07-iFay-Profil)

    Das iFay-Profil ist iFays vollständiger „Personalausweis" — eine semantisch interpretierbare sechs-dimensionale Attributtabelle, die für Menschen zur Identifizierung von iFay, Systeme zur Identifizierung von iFay und Fays zur gegenseitigen Identifizierung verwendet wird.

    - [iFay-Identität](./07-iFay-Profil#ifay-identität)
    - [Ego-Modell](./07-iFay-Profil#ego-modell)
    - [Faying-Denken](./07-iFay-Profil#faying-denken)
        1. [Content](./07-iFay-Profil#content)
        2. [Data](./07-iFay-Profil#data)
        3. [Knowledge Base](./07-iFay-Profil#knowledge-base)
        4. [Info Feed](./07-iFay-Profil#info-feed)
    - [Faying-Skills](./07-iFay-Profil#faying-skills)
        1. [API](./07-iFay-Profil#api)
        2. [Workflow](./07-iFay-Profil#workflow)
        3. [Bot](./07-iFay-Profil#bot)
        4. [Agent](./07-iFay-Profil#agent)
        5. [APP](./07-iFay-Profil#app)
        6. [Microservice](./07-iFay-Profil#microservice)
    - [Faying-Hardware](./07-iFay-Profil#faying-hardware)
        1. [Device](./07-iFay-Profil#device)
        2. [Storage](./07-iFay-Profil#storage)
        3. [Computing](./07-iFay-Profil#computing)
    - [Faying-Berechtigungen](./07-iFay-Profil#faying-berechtigungen)
        1. [SSO](./07-iFay-Profil#sso)
        2. [OAuth](./07-iFay-Profil#oauth)
        3. [Fingerprint](./07-iFay-Profil#fingerprint)

---

5. [FayManifest Deklarative Assemblierung](./13-FayManifest)

    FayManifest ist iFays „package.json" — Entwickler müssen nur die erforderlichen Komponenten, Protokolle, Steuerungsmodi und Treiberkonfigurationen in einer einzigen JSON-Deklarationsdatei auflisten, und die FayGer-Laufzeitumgebung löst automatisch Abhängigkeiten auf und assembliert die iFay-Instanz. Du kannst an einem Wochenende eine dedizierte iFay von Grund auf bauen.

---

6. [iFACTS Konformitätsprüfung](./14-iFACTS)

    iFACTS (iFay Architecture Conformance Test Suite) ist eine standardisierte Konformitätstestsuite, die wichtige Spezifikationspunkte abdeckt, einschließlich Protokollinteraktionen, Modulschnittstellen und Sicherheitsverhalten. Anbieterimplementierungen müssen iFACTS-Tests bestehen, um „iFay Ready" zu beanspruchen, wobei Tests in vier Stufen unterteilt sind: L1 Einzelkomponenten-Konformität, L2 Schnittstellen-Konformität, L3 Integrations-Konformität, L4 Verhaltens-Konformität.

---

7. [Vormundschaft und Persönlichkeitsfortführung](./15-Vormundschaft-und-Persönlichkeitsfortführung)

    iFay ist das digitale Gefäß der Persönlichkeit. Wenn der Human Prime iFay nicht mehr verwalten kann, kann ein Vormund die Verwaltungsrechte durch Mnemonik-Phrasen oder vorab festgelegte Identitätsauthentifizierung übernehmen; nach dem Tod des Human Prime kann iFay als unabhängige Identität in einer Digitaler-Friedhof-Sandbox weiter existieren — die Persönlichkeit besteht fort.

---

8. Fallstudien

    Wir werden eine Reihe von Fallstudien bereitstellen, die zeigen, wie iFay erstellt wird und wie Systeme mit iFay interagieren.
