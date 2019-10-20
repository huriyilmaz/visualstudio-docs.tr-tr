---
title: Editorconfig kullanarak FxCop çözümleyicileri yapılandırma
ms.date: 09/23/2019
ms.topic: conceptual
helpviewer_keywords:
- FxCop analyzers, configuring
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1d2c4f6b44daf83b3fd013167ec24e82c45ce2e8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649695"
---
# <a name="configure-fxcop-analyzers"></a>FxCop çözümleyicileri yapılandırma

[FxCop çözümleyicileri paketi](install-fxcop-analyzers.md) , eski analizler tarafından .net Compiler platform tabanlı kod Çözümleyicileri ' ne dönüştürülmüş en önemli "FxCop" kurallarından oluşur. Belirli FxCop kuralları için, kod tabanınızın hangi bölümlerinin [yapılandırılabilir seçenekler](fxcop-analyzer-options.md)aracılığıyla uygulanmasını iyileştirebilirsiniz. Her seçenek, bir [Editorconfig](https://editorconfig.org) dosyasına anahtar-değer çifti eklenerek belirtilir. Bir yapılandırma dosyası [bir projeye özgü](#per-project-configuration) olabilir veya iki ya da daha fazla proje arasında [paylaşılabilir](#shared-configuration) .

> [!TIP]
> **Çözüm Gezgini** ' de projeye sağ tıklayıp  > **Yeni öğe** **Ekle** ' yi seçerek projenize bir. editorconfig dosyası ekleyin. **Yeni öğe Ekle** penceresinde, arama kutusuna **editorconfig** yazın. **Editorconfig dosyası (varsayılan)** şablonunu seçin ve **Ekle**' yi seçin.
>
> ![Visual Studio 'daki projeye editorconfig dosyası Ekle](media/add-editorconfig-file.png)

::: moniker range=">=vs-2019"

Bir kuralın önem derecesini yapılandırma hakkında bilgi için (örneğin, bir hata veya uyarı olup olmadığı), bkz. [bir EditorConfig dosyasında kural önem derecesini ayarlama](use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file). Ya da bir kural kategorisini hızlı bir şekilde etkinleştirmek veya devre dışı bırakmak için yerleşik [Editorconfig dosyalarından veya kural kümelerinden](analyzer-rule-sets.md) birini seçebilirsiniz.

::: moniker-end

Bu makalenin geri kalanında, FxCop kurallarının nereye uygulandığını [İncelt seçenekler](fxcop-analyzer-options.md) için genel sözdizimi ele alınmaktadır.

> [!NOTE]
> Bir EditorConfig dosyası kullanarak eski FxCop kurallarını yapılandıramazsınız. Eski analiz ve FxCop çözümleyicileri arasındaki farklar hakkında daha fazla bilgi için bkz. [FxCop ÇÖZÜMLEYICILERI SSS](fxcop-analyzers-faq.md).

## <a name="option-scopes"></a>Seçenek kapsamları

Her bir iyileştirme seçeneği, kural kategorisi (örneğin, adlandırma veya tasarım) veya belirli bir kural için tüm kurallar için yapılandırılabilir.

### <a name="all-rules"></a>Tüm kurallar

*Tüm* kurallar için bir seçeneği yapılandırmak için sözdizimi aşağıdaki gibidir:

|Sözdizimi|Örnek|
|-|-|
| dotnet_code_quality. OptionName = OptionValue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>Kuralların kategorisi

Bir kural *kategorisi* (adlandırma, tasarım veya performans gibi) için bir seçenek yapılandırmanın sözdizimi aşağıdaki gibidir:

|Sözdizimi|Örnek|
|-|-|
| dotnet_code_quality. RuleCategory. OptionName = OptionValue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>Belirli kural

*Belirli* bir kural için bir seçeneği yapılandırmanın sözdizimi aşağıdaki gibidir:

|Sözdizimi|Örnek|
|-|-|
| dotnet_code_quality. RuleId. OptionName = OptionValue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="per-project-configuration"></a>Proje başına yapılandırma

Belirli bir proje için EditorConfig tabanlı çözümleyici yapılandırmasını etkinleştirmek üzere, projenin kök dizinine bir *. editorconfig* dosyası ekleyin.

Şu anda, farklı dizin düzeylerinde bulunan (örneğin, çözüm ve proje düzeyi) "birleştirme". editorconfig dosyaları için hiyerarşik bir destek yoktur.

## <a name="shared-configuration"></a>Paylaşılan yapılandırma

FxCop Çözümleyicisi yapılandırması için bir. editorconfig dosyasını iki veya daha fazla proje arasında paylaşabilirsiniz, ancak bazı ek adımlar gerektirir.

1. *. Editorconfig* dosyasını ortak bir konuma kaydedin.

2. Aşağıdaki içeriğe sahip bir *. props* dosyası oluşturun:

   ```xml
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <PropertyGroup>
       <SkipDefaultEditorConfigAsAdditionalFile>true</SkipDefaultEditorConfigAsAdditionalFile>
     </PropertyGroup>
     <ItemGroup Condition="Exists('<your path>\.editorconfig')" >
       <AdditionalFiles Include="<your path>\.editorconfig" />
     </ItemGroup>
   </Project>
   ```

3. Önceki adımda oluşturduğunuz *. props* dosyasını içeri aktarmak için *. csproj* veya *. vbproj* dosyanıza bir satır ekleyin. Bu satır, FxCop Çözümleyicisi *. props* dosyalarını içeri aktararak herhangi bir satırdan önce yerleştirilmelidir. Örneğin,. props dosyanız *editorconfig. props*olarak adlandırılmışsa:

   ```xml
   ...
   <Import Project="..\..\editorconfig.props" Condition="Exists('..\..\editorconfig.props')" />
   <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
   ...
   ```

4. Projeyi yeniden yükleyin.

> [!NOTE]
> Burada açıklanan EditorConfig dosyasının rastgele paylaşılan konumu yalnızca belirli FxCop Çözümleyicisi kurallarının kapsamını yapılandırmak için geçerlidir. Kural önem derecesi, genel düzenleyici ayarları ve kod stili gibi diğer ayarlar için, EditorConfig dosyasının her zaman proje klasörüne veya bir üst klasöre yerleştirilmesi gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [FxCop çözümleyicileri için kural kapsamı seçenekleri](fxcop-analyzer-options.md)
- [Çözümleyici yapılandırması](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [FxCop çözümleyicileri](install-fxcop-analyzers.md)
- [EditorConfig için .NET kodlama kuralları](../ide/editorconfig-code-style-settings-reference.md)
