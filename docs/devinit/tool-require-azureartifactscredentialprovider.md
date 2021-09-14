---
title: require-azureartifactscredentialprovider
description: devinit tool require-azureartifactscredentialprovider.
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
ms.openlocfilehash: e5ba9847b09f06f853f48a0885de5e0d63664fac
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725351"
---
# <a name="require-azureartifactscredentialprovider"></a>require-azureartifactscredentialprovider

> [!IMPORTANT]
> 12 Nisan 2021'den itibaren GitHub Codespaces'a Visual Studio 2019'dan bağlanmak artık desteklemeyecek ve bu özel önizlemenin sonucuna varıldı. Bulut destekli iç döngü için gelişen deneyimlere ve çok çeşitli iş yükleri için iyileştirilmiş VDI çözümlerine Visual Studio odaklanacağız. Bu ve ilişkili `devinit` araçların bir parçası olarak artık kullanılamaz. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi almak Visual Studio geliştirici topluluğu forummize dahil olmak için sizi teşvik ediyoruz.

Araç, `require-azureartifactscredentialprovider` Azure Artifacts Kimlik Bilgisi Sağlayıcı. Bu Azure Artifacts Kimlik Bilgisi Sağlayıcı, .NET geliştirme iş akışınız kapsamında NuGet geri yüklemek için gereken kimlik bilgilerinin alımını otomatik hale gelir. Burada daha fazla bilgi Azure Artifacts Kimlik Bilgisi Sağlayıcı [okuyun.](https://github.com/microsoft/artifacts-credprovider/blob/master/README.md)

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak [açıklanmış varsayılan](#default-behavior) davranışı takip eder.

| Ad                                             | Tür   | Gerekli | Değer                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **yorumlar**                                     | dize | No       | İsteğe bağlı açıklamalar özelliği. Kullanılmadı.                                                |
| [**Giriş**](#input)                              | dize | No       | Kullanılmadı. Ayrıntılar [için](#input) aşağıdaki girişe bakın. |
| [**additionalOptions**](#additional-options)     | dize | No       | Ayrıntılar [için aşağıdaki](#additional-options) Ek seçeneklere bakın.                     |

### <a name="input"></a>Giriş

Kullanılmadı. Varsa herhangi bir girişi yoksayar.

### <a name="additional-options"></a>Ek seçenekler

Ek seçenekler kimlik bilgisi sağlayıcısı komutuna olduğu gibi geçirilebilir.

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan `require-azureartifactscredentialprovider` davranışı, uygulamanın en son sürümünü Azure Artifacts Kimlik Bilgisi Sağlayıcı.

## <a name="example-usage"></a>Örnek kullanım
Aşağıda, kullanarak çalıştırmaya bir `require-azureartifactscredentialprovider` örnek `.devinit.json` verilmiştir.

#### <a name="devinitjson-that-will-install-azure-artifacts-credential-provider"></a>.devinit.json şu Azure Artifacts Kimlik Bilgisi Sağlayıcı:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-azureartifactscredentialprovider",
        }
    ]
}
```
