---
title: set-env
description: devinit tool require-set-env.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 86e6f7c22ac75d976050858eb2853f9036377fee
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725347"
---
# <a name="set-env"></a>set-env

> [!IMPORTANT]
> 12 Nisan 2021'den itibaren, Visual Studio 2019'dan GitHub Codespaces'a bağlanmak artık desteklemeyecek ve bu özel önizlemenin sonucuna varıldı. Bulut destekli iç döngü için gelişen deneyimlere ve çok çeşitli iş yükleri için iyileştirilmiş VDI çözümlerine Visual Studio odaklanacağız. Bu ve ilişkili `devinit` araçların bir parçası olarak artık kullanılamaz. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi almak Visual Studio geliştirici topluluğu forummize dahil olmak için sizi teşvik ediyoruz.

Araç, `set-env` geçerli işlemde kullanılacak ortam değişkenlerini ayarlamak için kullanılabilir. Ortam değişkenleri yalnızca geçerli işlemde ayarlanır ve bu işlemde `devinit` çalıştırısa diğer araçlar tarafından kullanılır.

Bu araç .NET Core `Environment.SetEnvironment` API'sini kullanır ve bu API ile aynı sınırlamalara sahiptir. Daha fazla bilgi için lütfen [belgelerine](/dotnet/api/system.environment.setenvironmentvariable?view=netcore-3.1&preserve-view=true) `Environment.SetEnvironment` bakın.

## <a name="usage"></a>Kullanım

| Ad                                         | Tür   | Gerekli | Değer                                                                       |
|----------------------------------------------|--------|----------|-----------------------------------------------------------------------------|
| **yorumlar**                                 | dize | No       | İsteğe bağlı açıklamalar özelliği. Kullanılmadı.                                       |
| [**Giriş**](#input)                          | dize | No       | Aracın girişi. Ayrıntılar [için](#input) aşağıdaki Giriş'e bakın.               |
| [**additionalOptions**](#additional-options) | dize | No       | Ayrıntılar [için aşağıdaki](#additional-options) Ek seçeneklere bakın.            |

### <a name="input"></a>Giriş

Araç, `set-env` özelliğine giriş olarak tek bir dize `input` alır. Dize, noktalı virgül (iki nokta üst üste) dizesi ;) sınırlandırılmış anahtar değer çiftleri (name=value) ve özelliğin değerine göre dört olası `input` eylem.

| Eylem       | Giriş            | Açıklama                                                                                                                                                              | Örnek             |
|--------------|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------|
| **hepsini listele** | boş veya atlanmış | Tüm geçerli ortam değişkenlerini listele.                                                                                                                           | `"input":""`        |
| **bir listele** | string           | Belirli bir ortam değişkeninin değerini adla listele.                                                                                                               | `"input":"foo"`     |
| **add**      | string           | Ortam değişkeninin değerini anahtar değer çifti olarak ayarlar. Henüz yoksa yeni bir ortam değişkeni ekler veya mevcut ortam değişkeninin değerini ayarlama | `"input":"foo=bar"` |
| **delete**   | string           | Boş bir değer dizesi geçerek mevcut bir ortam değişkenlerini siler.                                                                                            | `"input":"foo="`    |

Dize, `input` örneğin, değer okunurken `%userprofile%` genişletilen bir ortam değişkeni genişletmesi içerebilir.

### <a name="additional-options"></a>Ek seçenekler

 `--user`, `--process` veya , ortam `--machine` değişkenlerinin ayarlandırılacak yeri belirtmek için dahil olabilir. Varsayılan olarak, kullanıcıyı hedefleriz. Ortam değişkenleri için olası hedefler hakkında daha fazla bilgi için bkz. [EnvironmentVariableTarget](https://docs.microsoft.com/dotnet/api/system.environmentvariabletarget).

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan `set-env` davranışı, tüm geçerli ortam değişkenlerini listelemektedir.

## <a name="usage-in-a-codespace"></a>Codespace'de kullanım

Codespace kullanıyorsanız, dosyada özelliğini özelleştirerek codespace içinde kullanılan ortam `remoteEnv` değişkenlerini [`.devcontainer.json`](https://code.visualstudio.com/docs/remote/devcontainerjson-reference) ayarlayın.

## <a name="example-usage"></a>Örnek kullanım
Aşağıda, kullanarak çalıştırma örnekleri `set-env` `.devinit.json` verilmiştir.

#### <a name="devinitjson-that-will-set-an-environment-variable-foo-to-value-bar"></a>.devinit.json, değeri olarak bir ortam değişkeni `foo` `bar` ayarlar:
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "foo=bar",
    }
  ]
}
```

#### <a name="devinitjson-that-will-set-an-environment-variable-foo-to-value-bar-stored-in-the-environment-block-associated-with-the-current-process"></a>.devinit.json, geçerli işlemle ilişkili ortam bloğunda depolanan bir ortam değişkeni olan değerini , `foo` `bar` olarak ayarlar:
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "foo=bar",
      "additionalOptions": "--process",
    }
  ]
}
```

#### <a name="devinitjson-that-will-display-the-value-of-an-environment-variable"></a>Bir ortam değişkeninin değerini görüntüecek .devinit.json:
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "foo",
    }
  ]
}
```

#### <a name="devinitjson-that-will-list-all-the-environment-variables"></a>Tüm ortam değişkenlerini listeleyecek .devinit.json:
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
    }
  ]
}
```

#### <a name="devinitjson-that-will-delete-an-environment-variable"></a>Ortam değişkenlerini secek .devinit.json:
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "foo=",
    }
  ]
}
```


#### <a name="devinitjson-that-will-use-environment-variable-expansion"></a>Ortam değişkeni genişletmesini kullanan .devinit.json:
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "_savedPath=%path%",
    }
  ]
}
```

#### <a name="devinitjson-that-will-set-an-environment-variable-value-using-path-manipulation"></a>Yol işleme kullanarak ortam değişkeni değeri ayaracak .devinit.json:
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "path=%path%;%userprofile%\\CustomFolder",
    }
  ]
}
```

#### <a name="devinitjson-that-will-restore-path-from-saved-copy"></a>Kaydedilen kopyadan yolu geri yükleyecek .devinit.json:
```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-3.0",
  "run": [
    {
      "tool": "set-env",
      "input": "path=%_savedPath%",
    }
  ]
}
```
