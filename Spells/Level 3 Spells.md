## Counterspell
```GN
!servalias counterspell embed
{{set("level", int("%1%") if "%1"+"%"!="%1%" else 0)}}
{{set("dc", str(10+level))}}
{{set("mod", str(max(charismaMod, intelligenceMod, wisdomMod)))}}
{{set("result", vroll("1d20+" + mod))}}
{{set("success", (result.total>=int(dc)))}}
{{'-t "<name> attempts to counter the level %1% spell!"' if level else ''}}
{{'-desc "If it is a spell of a higher level than the spell slot you used, make an ability check using your spellcasting ability. The DC equals 10 + the spell\'s level. On a success, the creature\'s spell fails and has no effect."' if level else ''}}
{{('-f "DC|' + dc + '"') if level else ''}}
{{('-f "Ability Check|' + str(result) + '"') if level else ''}}
{{('-f "Result|' + ("Success" if success else "Failure") + '"') if level else ''}}
-color <color> -thumb <image>
```