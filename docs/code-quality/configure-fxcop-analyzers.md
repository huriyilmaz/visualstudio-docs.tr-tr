---
title: Editorconfig kullanarak .NET kod kalitesi Çözümleyicileri yapılandırma
ms.date: 09/23/2019
ms.topic: conceptual
helpviewer_keywords:
- .NET analyzers
- FxCop analyzers, configuring
- code quality
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a131b7d69eec61f9b9106f7a4274b3882c51f0ff
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88800742"
---
# <a name="configure-net-code-quality-analyzers"></a>.NET kod kalitesi Çözümleyicileri yapılandırma

Belirli .NET kod kalitesi Çözümleyicileri (kural kimlikleri ile başlayan `CA` ) için, kod tabanınızın hangi bölümlerinin [yapılandırılabilir seçenekler](fxcop-analyzer-options.md)aracılığıyla uygulanması gerektiğini iyileştirebilirsiniz. Her seçenek, bir [Editorconfig](https://editorconfig.org) dosyasına anahtar-değer çifti eklenerek belirtilir. Bir yapılandırma dosyası bir dosya, proje, çözüm veya tüm depoya özgü olabilir.

> [!TIP]
> **Çözüm Gezgini** ' de projeye sağ tıklayıp **Add**  >  **Yeni öğe**Ekle ' yi seçerek projenize bir. editorconfig dosyası ekleyin. **Yeni öğe Ekle** penceresinde, arama kutusuna **editorconfig** yazın. **Editorconfig dosyası (varsayılan)** şablonunu seçin ve **Ekle**' yi seçin.
>
> ![Visual Studio 'daki projeye editorconfig dosyası Ekle](media/add-editorconfig-file.png)

::: moniker range=">=vs-2019"

Bir kuralın önem derecesini yapılandırma hakkında bilgi için (örneğin, bir hata veya uyarı olup olmadığı), bkz. [bir EditorConfig dosyasında kural önem derecesini ayarlama](use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file). Ya da bir kural kategorisini hızlı bir şekilde etkinleştirmek veya devre dışı bırakmak için yerleşik [Editorconfig dosyalarından veya kural kümelerinden](analyzer-rule-sets.md) birini seçebilirsiniz.

::: moniker-end

Bu makalenin geri kalanında, .NET kod kalitesi Çözümleyicileri 'nin uygulanmasını [iyileştirmek](fxcop-analyzer-options.md) için genel sözdizimi ele alınmaktadır.

## <a name="option-scopes"></a>Seçenek kapsamları

Her bir iyileştirme seçeneği, kural kategorisi (örneğin, adlandırma veya tasarım) veya belirli bir kural için tüm kurallar için yapılandırılabilir.

### <a name="all-rules"></a>Tüm kurallar

*Tüm* kurallar için bir seçeneği yapılandırmak için sözdizimi aşağıdaki gibidir:

|Syntax|Örnek|
|-|-|
| dotnet_code_quality. OptionName = OptionValue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>Kuralların kategorisi

Bir kural *kategorisi* (adlandırma, tasarım veya performans gibi) için bir seçenek yapılandırmanın sözdizimi aşağıdaki gibidir:

|Syntax|Örnek|
|-|-|
| dotnet_code_quality. RuleCategory. OptionName = OptionValue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>Belirli kural

*Belirli* bir kural için bir seçeneği yapılandırmanın sözdizimi aşağıdaki gibidir:

|Syntax|Örnek|
|-|-|
| dotnet_code_quality. RuleId. OptionName = OptionValue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="enabling-editorconfig-based-configuration"></a>Editorconfig tabanlı yapılandırmayı etkinleştirme

Aşağıdaki kapsamlar için EditorConfig tabanlı çözümleyici yapılandırması etkinleştirilebilir:

- Belirli belge (ler)
- Belirli klasör (ler)
- Belirli proje (ler)
- Belirli çözümler
- Tüm depo

Yapılandırmayı etkinleştirmek için, karşılık gelen dizindeki seçeneklerle bir *. editorconfig* dosyası ekleyin. Bu dosya, EditorConfig tabanlı tanılama önem derecesi yapılandırma girdilerini de içerebilir. Daha ayrıntılı bilgi için [buraya](use-roslyn-analyzers.md#rule-severity) bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET kod kalitesi Çözümleyicileri için kural kapsamı seçenekleri](fxcop-analyzer-options.md)
- [Çözümleyici yapılandırması](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [EditorConfig için .NET kodlama kuralları](../ide/editorconfig-code-style-settings-reference.md)
