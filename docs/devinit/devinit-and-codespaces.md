---
title: devinit ve GitHub Codespaces
description: devinit kullanarak Visual Studio için bir codespace özelleştirmeyi öğrenin.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 377eb08e7255775b9d4bf187b0eb79c53499fe412b37c13ad6f1269d5a453c88
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121343397"
---
# <a name="devinit-and-github-codespaces"></a>devinit ve GitHub Codespaces

> [!IMPORTANT]
> 12 nisan 2021 itibariyle, Visual Studio 2019 ' den GitHub codespaces 'a bağlanmak artık desteklenmeyecektir ve bu özel önizleme sona ermiştir. bulut destekli bir iç döngü ve çok sayıda Visual Studio iş yükü için iyileştirilmiş vdı çözümleri için gelişen deneyimler üzerinde odaklanıyoruz. Bu `devinit` ve ilişkili araçların bir parçası olarak artık kullanılabilir olmayacaktır. gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi edinmek için Visual Studio geliştirici topluluğu forumumuza dahil etmeniz önerilir.

devınit [GitHub codespaces](https://github.com/features/codespaces) için harika bir tamamdır ve devinit, katkıda bulunanlar oluşturmak, çalıştırmak ve hata ayıklamak için hemen bir kod alanı kurulumu sağlamak üzere kullanılabilir.

> [!IMPORTANT]
> Devinit 'i codespace ile tümleştirmadan önce, bağımlılıklarınızı tanımlayan bir dosyaya sahip olduğunuzdan emin olmanız gerekir `.devinit.json` . Oluşturma hakkında daha fazla bilgi için Başlarken `.devinit.json` [belgelerini](getting-started-with-devinit.md)okuyun.

GitHub codespace içinde uygulamanız bulutta oluşturulup çalıştırılır. Bulutta olması, uygulamanızın makinelerinizdeki yerel kaynaklara erişimi olmadığı anlamına gelir. Bunlar yerel olarak yüklediğiniz araçları veya programları içerir. Uygulamanızın herhangi bir sistem genelinde bağımlılığı veya yapılandırılması gerekiyorsa, her bir codespace üzerinde yapılması gerekir. Bunu yapmanın en kolay yolu bir `.devinit.json` Dosya kullanmaktır.

Uygulamanızın ihtiyaç duyacağı bağımlılıklarla bir codespace oluşturulduğundan emin olmak için, `devinit` codespace oluşturulduğunda çalıştırılması gerekir. Bu, `devinit init` `postCreateCommand` Depo köküne yerleştirilmiş bir dosyada tanımlanan öğesinden çağırarak yapılabilir `.devcontainer.json` . İçindeki dize (ler), `postCreateCommand` Depo codespace 'e kopyalandıktan sonra varsayılan kabukta yürütülür. `postCreateCommand`GitHub codespaces [özelleştirme belgelerindeki](https://docs.github.com/github/developing-online-with-codespaces/configuring-codespaces-for-your-project)hakkında daha fazla bilgi edinebilirsiniz. Komutu eklemek için `devinit` `devinit init` `postCreateCommand` Aşağıdaki örneklerde gösterildiği gibi öğesine ekleyebilirsiniz.

codespace 'e bağlandıktan `devinit init -f <path to .devinit.json>` sonra, Visual Studio tümleşik terminalden da yürütebilirsiniz.

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

[belgelerimizde](sample-all-tool.md) devinit kullanmaya ilişkin daha fazla örnek ve [.net Core örneğinde](https://github.com/microsoft/devinit-example-dotnet-core) GitHub ve [örnek depolarıNode.js](https://github.com/microsoft/devinit-example-nodejs) bulabilirsiniz.

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
