---
title: set-env
description: devinit aracı gerekli-set-env.
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
ms.openlocfilehash: 89f62550d75a86c6d48848a31c99ca169964faa0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950430"
---
# <a name="set-env"></a>set-env

`set-env`Araç, geçerli işlemde kullanılmak üzere ortam değişkenlerini ayarlamak için kullanılabilir. Ortam değişkenleri yalnızca geçerli işlemde ayarlanır ve `devinit` Bu işlemde çalıştırıldıklarında diğer araçlar tarafından kullanılır.

Bu araç .NET Core API 'sini kullanır `Environment.SetEnvironment` ve bu API ile aynı sınırlamalara sahiptir. Daha fazla bilgi için lütfen [belgelerine](/dotnet/api/system.environment.setenvironmentvariable?view=netcore-3.1&preserve-view=true) bakın `Environment.SetEnvironment` .

## <a name="usage"></a>Kullanım

| Ad                                         | Tür   | Gerekli | Değer                                                                       |
|----------------------------------------------|--------|----------|-----------------------------------------------------------------------------|
| **açıklamaları**                                 | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                       |
| [**girişinin**](#input)                          | dize | No       | Araca giriş. Ayrıntılar için aşağıdaki [girişi](#input) inceleyin.               |
| [**additionalOptions**](#additional-options) | dize | No       | Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.            |

### <a name="input"></a>Giriş

`set-env`Araç, özellikte giriş olarak tek bir dize alır `input` . Dize, noktalı virgül (;)) dizesi olarak biçimlendirilmelidir özelliğin değerine göre ayrılmış anahtar değeri çiftleri (ad = değer) ve dört olası eylem `input` .

| Eylem       | Giriş            | Açıklama                                                                                                                                                              | Örnek             |
|--------------|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------|
| **Tümünü Listele** | boş veya atlanmış | Tüm geçerli ortam değişkenlerini listeleyin.                                                                                                                           | `"input":""`        |
| **liste bir** | string           | Belirli bir ortam değişkeninin değerini ada göre listeleyin.                                                                                                               | `"input":"foo"`     |
| **add**      | string           | Bir ortam değişkeninin değerini anahtar değer çifti olarak ayarlar. Henüz yoksa yeni bir ortam değişkeni ekler veya var olan bir ortam değişkeninin değerini ayarlar | `"input":"foo=bar"` |
| **delete**   | string           | Boş bir değer dizesini geçirerek var olan bir ortam değişkenini siler.                                                                                            | `"input":"foo="`    |

Bir `input` dize `%userprofile%` , örneğin değer okuma olduğunda genişletilen bir ortam değişkeni genişletmesi içerebilir.

### <a name="additional-options"></a>Ek seçenekler

 `--user`, `--process` veya `--machine` ortam değişkenlerinin nerede ayarlanacağını belirtmek için dahil edilebilir. Varsayılan olarak, kullanıcıyı hedefliyoruz. Ortam değişkenlerinin olası hedefleri hakkında daha fazla bilgi için bkz. [EnvironmentVariableTarget](https://docs.microsoft.com/dotnet/api/system.environmentvariabletarget).

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan davranışı, `set-env` tüm geçerli ortam değişkenlerini listeleridir.

## <a name="usage-in-a-codespace"></a>Codespace 'teki kullanım

Codespace kullanıyorsanız, dosyadaki özelliği özelleştirerek codespace 'te kullanılan ortam değişkenlerini ayarlayabilirsiniz `remoteEnv` [`.devcontainer.json`](/visualstudio/codespaces/reference/configuring) .

## <a name="example-usage"></a>Örnek kullanım
Kullanarak nasıl çalıştırılacağını gösteren örnekler aşağıda verilmiştir `set-env` `.devinit.json` .

#### <a name="devinitjson-that-will-set-an-environment-variable-foo-to-value-bar"></a>Üzerinde .devinit.js, bir ortam değişkeni ayarlanacak, `foo` değer `bar` :
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

#### <a name="devinitjson-that-will-set-an-environment-variable-foo-to-value-bar-stored-in-the-environment-block-associated-with-the-current-process"></a>Üzerinde .devinit.js, `foo` `bar` geçerli işlemle ilişkili ortam bloğunda depolanan bir ortam değişkenini değere ayarlayacaktır:
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

#### <a name="devinitjson-that-will-display-the-value-of-an-environment-variable"></a>.devinit.js, bir ortam değişkeninin değerini görüntüleyecektir:
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

#### <a name="devinitjson-that-will-list-all-the-environment-variables"></a>Tüm ortam değişkenlerini listeedilecek .devinit.js:
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

#### <a name="devinitjson-that-will-delete-an-environment-variable"></a>.devinit.js, bir ortam değişkenini silecek:
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


#### <a name="devinitjson-that-will-use-environment-variable-expansion"></a>.devinit.js, ortam değişkeni genişletmeyi kullanacak:
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

#### <a name="devinitjson-that-will-set-an-environment-variable-value-using-path-manipulation"></a>.devinit.js, yol işleme kullanarak bir ortam değişken değeri ayarlar:
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

#### <a name="devinitjson-that-will-restore-path-from-saved-copy"></a>.devinit.js, kaydedilen kopyadan yolu geri yükler:
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
