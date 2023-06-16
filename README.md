<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

Doporučuje se nejprve nainstalovat nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) a po vstupu do adresáře pak `direnv allow` ( [.envrc](https://github.com/xxai-art/doc/blob/main/.envrc) se spustí automaticky po vstupu do adresáře).

Význam je: čínský překlad do japonštiny, korejštiny, angličtiny, anglický překlad do všech ostatních jazyků. Pokud chcete podporovat pouze čínštinu a angličtinu, stačí napsat `zh: en` .

Význam je: čínský překlad do japonštiny, korejštiny, angličtiny, anglický překlad do všech ostatních jazyků. Pokud chcete podporovat pouze čínštinu a angličtinu, stačí napsat `zh: en` .

* [front-end kód](https://github.com/xxai-art/web)
* [Jazykové balíčky pro web jako celek](https://github.com/xxai-art/web/tree/main/i18n)
* [Jazykové balíčky pro přihlašovací moduly](https://github.com/wacpkg/user/tree/main/ui.i18n)
* [Webová vícejazyčná dokumentace](https://github.com/xxai-doc)

Front-end programovací jazyk je [@w5/coffee_plus](http://npmjs.com/@w5/coffee_plus) , který přidává některé funkce založené na syntaxi coffeescriptu, viz [./coffee_plus.md](./coffee_plus.md) .

## Internacionalizace webových stránek a dokumentů

Stavte na následujících 3 projektech

* [@w5/mdt](https://www.npmjs.com/package/@w5/mdt)

  Přípona je `.mdt` , můžete použít syntaxi podobnou `<+ ./coffee_plus/import.js>` k odkazování na externí soubory a generovat markdown s příponou `.md` .

* [@w5/trmd](https://www.npmjs.com/package/@w5/trmd)

  Překlad Markdown nepřekládá kódy a odkazy a ukládá přeložené věty do mezipaměti. Pokud je překlad upraven, ale původní text není upraven, jeho opětovné provedení nepřepíše úpravu překladu.

* [@w5/i18n](https://www.npmjs.com/package/@w5/i18n)

  Jazykové soubory pro překlad webových stránek generovaných `yaml` .

### Pokyny pro automatizaci překladu dokumentů

Viz úložiště kódu [xxai-art/doc](https://github.com/xxai-art/doc)

Doporučuje se nejprve nainstalovat nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) a po vstupu do adresáře pak `direnv allow` ( [.envrc](https://github.com/xxai-art/doc/blob/main/.envrc) se spustí automaticky po vstupu do adresáře).

Abych se vyhnul velké kódové základně překládané do stovek jazyků, vytvořil jsem samostatnou kódovou základnu pro každý jazyk a vytvořil jsem organizaci pro uložení kódové základny.

Nastavení proměnné prostředí `GITHUB_ACCESS_TOKEN` a následné spuštění [create.github.coffee](https://github.com/xxai-art/doc/blob/main/create.github.coffee) automaticky vytvoří úložiště kódu.

Samozřejmě to můžete také vložit do kódové základny.

Odkaz na překladový skript [run.sh](https://github.com/xxai-art/doc/blob/main/run.sh)

Kód skriptu je interpretován následovně:

[bunx](https://bun.sh/docs/cli/bunx) je náhrada za npx, který je rychlejší. Samozřejmě, pokud nemáte nainstalovaný bun, můžete místo toho použít `npx` .

`bunx mdt zh` vykreslí `.mdt` v adresáři zh jako `.md` , viz 2 propojené soubory níže

* [coffee_plus.mdt](https://github.com/xxai-doc/zh/blob/main/coffee_plus.mdt)
* [coffee_plus.md](https://github.com/xxai-doc/zh/blob/main/coffee_plus.md)

`bunx i18n` je základní kód pro překlad (pokud máte nainstalovaný pouze `nodejs` , ale nejsou nainstalovány `bun` a `direnv` , můžete k překladu spustit také `npx i18n` ).

Bude analyzovat [i18n.yml](https://github.com/xxai-art/doc/blob/main/i18n.yml) , konfigurace `i18n.yml` v tomto dokumentu je následující:

```
en:
zh: ja ko en
```

Význam je: čínský překlad do japonštiny, korejštiny, angličtiny, anglický překlad do všech ostatních jazyků. Pokud chcete podporovat pouze čínštinu a angličtinu, stačí napsat `zh: en` .

Poslední je [gen.README.coffee](https://github.com/xxai-art/doc/blob/main/gen.README.coffee) , která extrahuje obsah mezi hlavním názvem a prvním titulkem souboru `README.md` každého jazyka a vygeneruje záznam `README.md` . Kód je velmi jednoduchý, můžete se na něj podívat sami.

Pro bezplatný překlad se používá Google API. Pokud nemáte přístup ke Google, nakonfigurujte a nastavte proxy, například:

```
export https_proxy=http://127.0.0.1:7890 http_proxy=http://127.0.0.1:7890 all_proxy=socks5://127.0.0.1:7890
```

Překladový skript vygeneruje přeloženou mezipaměť v adresáři `.i18n` , zkontrolujte ji pomocí `git status` a přidejte ji do úložiště kódu, abyste předešli opakovaným překladům.

Spusťte prosím `bunx i18n` pokaždé, když změníte překlad pro aktualizaci mezipaměti.

Pokud jsou původní text a překlad upraveny současně, mezipaměť bude zmatená, takže pokud chcete upravit, můžete upravit pouze jednu a poté spustit `bunx i18n` pro aktualizaci mezipaměti.
