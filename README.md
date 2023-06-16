<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

# xxAI.art

Část kódu webových stránek je open source, vítáme vás, abyste pomohli optimalizovat překlad.

## front-end kód

* [front-end kód](https://github.com/xxai-art/web)
* [Jazykové balíčky pro web jako celek](https://github.com/xxai-art/web/tree/main/i18n)
* [Jazykové balíčky pro přihlašovací moduly](https://github.com/wacpkg/user/tree/main/ui.i18n)
* [Webová vícejazyčná dokumentace](https://github.com/xxai-doc)

Front-end programovací jazyk je [@w5/coffee_plus](http://npmjs.com/@w5/coffee_plus) , který přidává některé funkce založené na syntaxi coffeescriptu, viz [./coffee_plus.md](./coffee_plus.md) .

## Internacionalizace webových stránek a dokumentů

Stavte na následujících 3 projektech

### [@w5/mdt](https://www.npmjs.com/package/@w5/mdt)

Šablona markdown s příponou `.mdt` může odkazovat na externí soubory se syntaxí podobnou `<+ ./coffee_plus/import.js>` .

[@w5/trmd](https://www.npmjs.com/package/@w5/trmd)

Překlad Markdown nepřekládá kódy a odkazy a ukládá přeložené věty do mezipaměti. Pokud je překlad upraven, ale původní text není upraven, jeho opětovné provedení nepřepíše úpravu překladu.

[@w5/i18n](https://www.npmjs.com/package/@w5/i18n)

Jazykové soubory pro překlad webových stránek generovaných `yaml` .
