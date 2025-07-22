# Smlouvator

**Smlouvator** je jednoduchá Python aplikace pro generování smluv ve formátu Microsoft Word (.docx) na základě šablon s dynamickým doplňováním údajů.

## Co Smlouvator umí
- Vybrat typ smlouvy ze šablon (.docx)
- Vybrat firmu ze seznamu firem uložených v `firmy.json`
- Automaticky doplnit údaje o firmě do šablony
- Zeptat se uživatele na zbývající údaje (např. jméno zaměstnance, datumy atd.)
- Vytvořit finální dokument do složky `Smlouvy` s automatickým pojmenováním souboru

## Struktura projektu

```
smlouvator/
├── firmy.json          # Seznam firem
├── templates/          # Složka se šablonami smluv
├── Smlouvy/            # Výstupní složka pro hotové smlouvy
└── main.py             # Hlavní skript aplikace
```

## Instalace

1. Ujisti se, že máš nainstalovaný Python 3.8+.
2. Doporučeno: vytvoř si virtuální prostředí.
3. Nainstaluj potřebné balíčky:
```bash
pip install -r requirements.txt
```

### Potřebné knihovny
- `python-docx`
- `questionary` – hezčí CLI rozhraní
- `docx2pdf` – export do PDF (Windows/Mac)

## Použití

1. Přidej své šablony smluv do složky `templates/`. Šablona obsahuje placeholdery ve formátu `{placeholder}`.
2. Přidej své firmy do souboru `firmy.json`. Příklad:
```json
[
  {
    "nazev": "Example s.r.o.",
    "ico": "12345678",
    "adresa": "Ulice 123, 100 00 Praha",
    "zastoupena": "Jan Novák, jednatel",
    "vedena": "Městský soud v Praze, oddíl C, vložka 123456"
  }
]
```
3. Spusť skript:
```bash
python main.py
```
4. Postupuj podle pokynů v terminálu.
5. Po vyplnění údajů se aplikace zeptá, zda chcete vytvořit i PDF verzi smlouvy.

## Výstupní soubory
Hotové smlouvy se ukládají do složky `Smlouvy/` a jejich název je automaticky generován podle vzoru:
```
[Příjmení] [Jméno]_[Firma]_[název_smlouvy_podle_template]_[měsíc nástupu][rok nástupu].docx
```

## Licence
MIT licence.