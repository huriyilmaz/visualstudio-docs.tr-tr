---
title: set-env
description: devinit aracı gerekli-set-env.
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
ms.openlocfilehash: 2f4ec5489f22e94ad8f57f22ddc7742dc0ae3ade
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005997"
---
# <a name="set-env"></a>set-env

`set-env`Araç, geçerli işlemde kullanılmak üzere ortam değişkenlerini ayarlamak için kullanılabilir. Ortam değişkenleri yalnızca geçerli işlemde ayarlanır ve `devinit` Bu işlemde çalıştırıldıklarında diğer araçlar tarafından kullanılır.

Bu araç .NET Core API 'sini kullanır `Environment.SetEnvironment` ve bu API ile aynı sınırlamalara sahiptir. Daha fazla bilgi için lütfen [belgelerine](https://docs.microsoft.com/dotnet/api/system.environment.setenvironmentvariable?view=netcore-3.1&preserve-view=true) bakın `Environment.SetEnvironment` .

## <a name="usage"></a>Kullanım

| Ad                                         | Tür   | Gerekli | Değer                                                                       |
|----------------------------------------------|--------|----------|-----------------------------------------------------------------------------|
| **açıklamaları**                                 | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                       |
| [**girişinin**](#input)                          | dize | No       | Araca giriş. Ayrıntılar için aşağıdaki [girişi](#input) inceleyin.               |
| [**additionalOptions**](#additional-options) | dize | No       | Kullanılmadı. Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.  |

### <a name="input"></a>Giriş

`set-env`Araç, özellikte giriş olarak tek bir dize alır `input` . Dize, noktalı virgül (;)) dizesi olarak biçimlendirilmelidir özelliğin değerine göre ayrılmış anahtar değeri çiftleri (ad = değer) ve dört olası eylem `input` .

| Eylem       | Giriş            | Açıklama                                                                                                                                                              | Örnek             |
|--------------|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------|
| **Tümünü Listele** | boş veya atlanmış | Tüm geçerli ortam değişkenlerini listeleyin.                                                                                                                              | `"input":""`        |
| **liste bir** | string           | Belirli bir ortam değişkeninin değerini ada göre listeleyin.                                                                                                               | `"input":"foo"`     |
| **add**      | string           | Bir ortam değişkeninin değerini anahtar değer çifti olarak ayarlar. Henüz yoksa yeni bir ortam değişkeni ekler veya var olan bir ortam değişkeninin değerini ayarlar | `"input":"foo=bar"` |
| **delete**   | string           | Boş bir değer dizesini geçirerek var olan bir ortam değişkenini siler.                                                                                            | `"input":"foo="`    |

Bir `input` dize `%userprofile%` , örneğin değer okuma olduğunda genişletilen bir ortam değişkeni genişletmesi içerebilir.

### <a name="additional-options"></a>Ek seçenekler

Kullanılmadı.

## <a name="usage-in-a-codespace"></a>Codespace 'teki kullanım

Bir codespace kullanıyorsanız, codespace 'te kullanılan ortam değişkenlerini, customizating özelliğini kullanarak belirleyebilirsiniz `remoteEnv` [`.devcontainer.json`](https://docs.microsoft.com/visualstudio/codespaces/reference/configuring) .

## <a name="example-usage"></a>Örnek kullanım

```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-2.0",
  "comments": "A sample dot-devinit file demonstrating the set-env tool.",
  "run": [
    {
      "tool": "set-env",
      "input": "foo=bar",
      "comments": "To set an environment variable, set input to 'name=value'."
    },
    {
      "tool": "set-env",
      "input": "foo",
      "comments": "To display the value of a single environment variable, set input to the name of the variable."
    },
    {
      "tool": "set-env",
      "comments": "To list all environment variables, pass no input."
    },
    {
      "tool": "set-env",
      "input": "foo=",
      "comments": "To delete an environment variable, pass input of 'name='."
    },
    {
      "tool": "set-env",
      "input": "foo",
      "comments": "Trying to display a variable that doesn't exist results in a warning."
    },
    {
      "tool": "set-env",
      "input": "_savedPath=%path%",
      "comments": "Envrionment variable expansion is supported."
    },
    {
      "tool": "set-env",
      "input": "path=%path%;%userprofile%\\CustomFolder",
      "comments": "Shows path manipulation. Note: Variables set here are not persisted."
    },
    {
      "tool": "set-env",
      "input": "path=%_savedPath%",
      "comments": "Restore path from saved copy."
    }
  ]
}
```
