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
ms.openlocfilehash: 7ba3ff8e22923590c21333c35563a98352eeef21
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94438238"
---
# <a name="devinit-and-github-codespaces"></a>devinit ve GitHub Codespaces

devinit, [GitHub codespace](https://github.com/features/codespaces) 'e harika bir fikir ve devinit, katkıda bulunanlar oluşturmak, çalıştırmak ve hata ayıklamak için hemen bir kod alanı kurulumu sağlamak üzere kullanılabilir.

> [!IMPORTANT]
> Devinit 'i codespace ile tümleştirmadan önce, bağımlılıklarınızı tanımlayan bir dosyaya sahip olduğunuzdan emin olmanız gerekir `.devinit.json` . Oluşturma hakkında daha fazla bilgi için Başlarken `.devinit.json` [belgelerini](getting-started-with-devinit.md)okuyun.

GitHub Codespace içinde uygulamanız bulutta oluşturulup çalıştırılır. Bulutta olması, uygulamanızın makinelerinizdeki yerel kaynaklara erişimi olmadığı anlamına gelir. Bunlar yerel olarak yüklediğiniz araçları veya programları içerir. Uygulamanızın herhangi bir sistem genelinde bağımlılığı veya yapılandırılması gerekiyorsa, her bir codespace üzerinde yapılması gerekir. Bunu yapmanın en kolay yolu bir `.devinit.json` Dosya kullanmaktır.

Uygulamanızın ihtiyaç duyacağı bağımlılıklarla bir codespace oluşturulduğundan emin olmak için, `devinit` codespace oluşturulduğunda çalıştırılması gerekir. Bu, `devinit init` `postCreateCommand` Depo köküne yerleştirilmiş bir dosyada tanımlanan öğesinden çağırarak yapılabilir `.devcontainer.json` . İçindeki dize (ler), `postCreateCommand` Depo codespace 'e kopyalandıktan sonra varsayılan kabukta yürütülür. `postCreateCommand`GitHub Codespaces [Özelleştirme belgelerindeki](https://docs.github.com/github/developing-online-with-codespaces/configuring-codespaces-for-your-project)hakkında daha fazla bilgi edinebilirsiniz. Komutu eklemek için `devinit` `devinit init` `postCreateCommand` Aşağıdaki örneklerde gösterildiği gibi öğesine ekleyebilirsiniz.

Codespace 'e bağlandıktan `devinit init -f <path to .devinit.json>` sonra Visual Studio tümleşik terminalden da çalıştırabilirsiniz.

## <a name="examples"></a>Örnekler

Aşağıdaki örneklerde her iki örnekte de `.devinit.json` Depo kökünde bulunur `.devcontainer.json` .

### <a name="with-a-devcontainerjson-file"></a>.devcontainer.jsdosya ile

Bu örnekte, `.devcontainer.json` aşağıdaki dosya, dosyanın yanı sıra depo köküne yerleştirilir `.devinit.json` . Dosyalar da bir `.devcontainer` dizine yerleştirilebilir.

```json
{
  "postCreateCommand": "devinit init"
}
```

`.devinit.json`Başka bir dizinde olduğunda-f bayrağı kullanılabilir.

```json
{
  "postCreateCommand": "devinit init -f path\\to\\.devinit.json"
}

```

```json
{
  "postCreateCommand": ["<some other command>", "devinit init"]
}
```

Devinit ' i [belgelerimizde](sample-all-tool.md) ve GitHub ' da [.net Core örneğinde](https://github.com/microsoft/devinit-example-dotnet-core) [Node.js ve örnek](https://github.com/microsoft/devinit-example-nodejs) depolarda kullanmak için daha fazla örnek bulabilirsiniz.

### <a name="as-commands"></a>As komutları

Bu örnekte, `.devcontainer.json` aşağıdaki dosya depo köküne yerleştirilir ve `devinit run` tek bir aracı çalıştırmak için komut satırından doğrudan çağırılır.  

```json
{
  "postCreateCommand": ["devinit run –t require-dotnetcoresdk"]
}
```

### <a name="from-a-terminal-prompt"></a>Terminal isteminden

Geçerli çalışma dizini bir `.devinit.json` Dosya içerdiğinde.

```console
devinit init
```

`.devinit.json`Başka bir dizinde olduğunda.

```console
devinit init -f path/to/.devinit.json
```
