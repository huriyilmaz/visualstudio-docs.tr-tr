---
title: devinit ve GitHub Codespaces
description: Devinit kullanarak Visual Studio için bir codespace özelleştirmeyi öğrenin.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: a9731469f6725c0a4b9118c4e41235974a19c473
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93134387"
---
# <a name="devinit-and-github-codespaces"></a>devinit ve GitHub Codespaces

devinit, [GitHub codespace](https://github.com/features/codespaces) 'e harika bir fikir ve devinit, katkıda bulunanlar oluşturmak, çalıştırmak ve hata ayıklamak için hemen bir kod alanı kurulumu sağlamak üzere kullanılabilir.

GitHub Codespaces ile tümleştirilmesi için, `devinit` `postCreateCommand` `.devcontainer.json` Depo köküne yerleştirilmiş bir dosyada tanımlanan öğesinden çağrılmalıdır. İçindeki dize (ler), `postCreateCommand` Depo codespace 'e kopyalandıktan sonra varsayılan kabukta yürütülür. `postCreateCommand`GitHub Codespaces [Özelleştirme belgelerindeki](https://docs.github.com/github/developing-online-with-codespaces/configuring-codespaces-for-your-project)hakkında daha fazla bilgi edinebilirsiniz. Komutu eklemek için `devinit` `devinit init` `postCreateCommand` Aşağıdaki örneklerde gösterildiği gibi öğesine ekleyebilirsiniz.

Codespace 'e bağlandıktan `devinit init -f <path to .devinit.json>` sonra Visual Studio tümleşik terminalden da çalıştırabilirsiniz.

## <a name="examples"></a>Örnekler

### <a name="with-a-devinitjson-file"></a>.devinit.jsdosya ile
Bu örnekte, aşağıdaki dosyadaki _.devcontainer.js_ , _.devinit.json_ dosyası ile birlikte depo köküne yerleştirilir. Dosyalar bir _. devcontainer_ dizinine de yerleştirilebilecek.

```json
{
  "postCreateCommand": "devinit init"
}
```

```json
{
  "postCreateCommand": ["<some other command>", "devinit init"]
}
```

### <a name="as-commands"></a>As komutları
Bu örnekte _.devcontainer.js_ aşağıdaki dosya depo köküne yerleştirildi ve `devinit run` bir aracı çalıştırmak için programlı olarak çağırılır  

```json
{
  "postCreateCommand": ["devinit run –t require-dotnetcoresdk"]
}
```

### <a name="from-a-terminal-prompt"></a>Terminal isteminden

Geçerli çalışma dizini bir _.devinit.js_ dosya içerdiğinde.

```console
devinit init
```

_.devinit.js_ , başka bir dizinde olduğunda.

```console
devinit init -f path/to/.devinit.json
```
