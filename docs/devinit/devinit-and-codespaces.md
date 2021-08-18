---
title: devinit ve GitHub Codespaces
description: devinit kullanarak bir codespace'ı Visual Studio öğrenin.
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
> 12 Nisan 2021'den itibaren Visual Studio 2019'dan GitHub Codespaces'a bağlanma desteklemeyecek ve bu özel önizleme sonuçlandırıldı. Bulut destekli iç döngü için gelişen deneyimlere ve çok çeşitli iş yükleri için iyileştirilmiş VDI çözümlerine Visual Studio odaklanacağız. Bu ve ilişkili `devinit` araçların bir parçası olarak artık kullanılamaz. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi için Visual Studio geliştirici topluluğu forummize katılın.

devinit, [Codespaces'GitHub](https://github.com/features/codespaces) için harika bir tamamlayıcıdır ve katkıda bulunanların hemen derleme, çalıştırma ve hata ayıklaması için codespace kurulumu almak için kullanılabilir.

> [!IMPORTANT]
> sapını codespace ile tümleştirmeden önce bağımlılıklarınızı tanımlayan bir `.devinit.json` dosyanız olduğundan emin olun. oluşturma hakkında daha fazla bilgi `.devinit.json` için, başlarken [belgelerini okuyun.](getting-started-with-devinit.md)

Codespace'GitHub içinde, uygulamanız bulutta yerleşik olarak ve çalıştırabilirsiniz. Bulutta olmak, uygulamanın makineleriniz üzerinde yerel kaynaklara erişimi olmadığını anlamına gelir. Bunlar, yerel olarak yüklemiş olduğunuz araçları veya programları içerir. Uygulamanıza tüm sistem genelinde bağımlılıkların yüklenmiş veya yapılandırılmış olması gerekirse, her codespace üzerinde yapılması gerekir. Bunu başarmanın en kolay yolu bir dosya `.devinit.json` kullanmaktır.

Bir codespace'in, uygulamanıza gereken bağımlılıklarla oluşturulduktan emin olmak için `devinit` codespace oluşturulduğunda çalıştırılan olması gerekir. Bu, depo `devinit init` köküne yerleştirilen `postCreateCommand` bir dosyada `.devcontainer.json` tanımlanan çağrısıyla yapılabilir. 'daki dizeler, codespace'da repo `postCreateCommand` kopyalandıktan sonra varsayılan kabukta yürütülür. `postCreateCommand`Codespaces özelleştirme belgelerinin GitHub daha [fazla bilgi edinebilirsiniz.](https://docs.github.com/github/developing-online-with-codespaces/configuring-codespaces-for-your-project) Komutu eklemek `devinit` için, aşağıdaki `devinit init` örneklerde gösterildiği gibi `postCreateCommand` komutuna indirebilirsiniz.

Codespace'inize `devinit init -f <path to .devinit.json>` bağlandıktan Visual Studio Tümleşik Terminal'den de yürütebilirsiniz.

## <a name="examples"></a>Örnekler

Aşağıdaki her iki örnekte `.devinit.json` de , ile birlikte depo kökündedir. `.devcontainer.json`

### <a name="with-a-devcontainerjson-file"></a>Bir .devcontainer.jsdosyasıyla

Bu örnekte, `.devcontainer.json` aşağıdaki dosya, dosyanın yanı sıra repo köküne `.devinit.json` yerleştirilir. Dosyalar bir dizine de `.devcontainer` yerleştirilebilirsiniz.

```json
{
  "postCreateCommand": "devinit init"
}
```

başka `.devinit.json` bir dizinde olduğunda , -f bayrağı kullanılabilir.

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

.NET [Core](https://github.com/microsoft/devinit-example-dotnet-core) örneğinde ve örnek [](sample-all-tool.md) depolarda yer alan belgelerde ve GitHub kullanarak [daha fazlaNode.js](https://github.com/microsoft/devinit-example-nodejs) bulabilirsiniz.

### <a name="as-commands"></a>As komutları

Bu örnekte aşağıdaki dosya, tek bir aracı çalıştırmak için doğrudan komut satırına çağrılır ve aşağıdaki `.devcontainer.json` `devinit run` dosya, bir repo köküne yerleştirilir.  

```json
{
  "postCreateCommand": ["devinit run –t require-dotnetcoresdk"]
}
```

### <a name="from-a-terminal-prompt"></a>Terminal isteminden

Geçerli çalışma dizini bir dosya `.devinit.json` içerdiğinde.

```console
devinit init
```

başka `.devinit.json` bir dizinde olduğunda.

```console
devinit init -f path/to/.devinit.json
```
