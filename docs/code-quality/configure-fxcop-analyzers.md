---
title: Editorconfig kullanarak .NET kod kalitesi Çözümleyicileri yapılandırma
ms.date: 09/01/2020
ms.topic: conceptual
helpviewer_keywords:
- .NET analyzers
- FxCop analyzers, configuring
- code quality
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: bc237082ec1188d71241facead975db1df2cf3af
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90035436"
---
# <a name="configure-net-code-quality-analysis-with-editorconfig"></a>.NET Code Quality analizini EditorConfig ile yapılandırma

Her kod kalitesi Çözümleyicisi (kural kimlikleri ile başlayan `CA` ), yapılandırılabilir seçenekler aracılığıyla kod tabanınızın bölümlerine uygulanacak şekilde iyileştirilmelidir. Her seçenek, bir [Editorconfig](https://editorconfig.org) dosyasına anahtar-değer çifti eklenerek belirtilir. Bir yapılandırma dosyası bir dosya, proje, çözüm veya tüm depoya özgü olabilir.

> [!TIP]
> **Çözüm Gezgini** ' de projeye sağ tıklayıp **Add**  >  **Yeni öğe**Ekle ' yi seçerek projenize bir. editorconfig dosyası ekleyin. **Yeni öğe Ekle** penceresinde, arama kutusuna **editorconfig** yazın. **Editorconfig dosyası (varsayılan)** şablonunu seçin ve **Ekle**' yi seçin.
>
> ![Visual Studio 'daki projeye EditorConfig dosyası Ekle](media/add-editorconfig-file.png)

::: moniker range=">=vs-2019"

Bir kuralın önem derecesini yapılandırma hakkında bilgi için (örneğin, bir hata veya uyarı olup olmadığı), bkz. [bir EditorConfig dosyasında kural önem derecesini ayarlama](use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file). Ya da bir kural kategorisini hızlı bir şekilde etkinleştirmek veya devre dışı bırakmak için yerleşik [Editorconfig dosyalarından veya kural kümelerinden](analyzer-rule-sets.md) birini seçebilirsiniz.

::: moniker-end

Bu makalenin geri kalanında, .NET kod kalitesi Çözümleyicileri 'nin uygulanmasını iyileştirmek için genel sözdizimi ele alınmaktadır.

## <a name="option-scopes"></a>Seçenek kapsamları

Her bir iyileştirme seçeneği, kural kategorisi (örneğin, güvenlik veya tasarım) veya belirli bir kural için tüm kurallar için yapılandırılabilir.

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

## <a name="enabling-editorconfig-based-configuration"></a>EditorConfig tabanlı yapılandırmayı etkinleştirme

Aşağıdaki kapsamlar için EditorConfig tabanlı çözümleyici yapılandırması etkinleştirilebilir:

- Belirli belge (ler)
- Belirli klasör (ler)
- Belirli proje (ler)
- Belirli çözümler
- Tüm depo

Yapılandırmayı etkinleştirmek için, karşılık gelen dizindeki seçeneklerle bir *. editorconfig* dosyası ekleyin. Bu dosya, EditorConfig tabanlı tanılama önem derecesi yapılandırma girdilerini de içerebilir. Daha ayrıntılı bilgi için [buraya](use-roslyn-analyzers.md#configure-severity-levels) bakın.

## <a name="enable-a-category-of-rules"></a>Kural kategorisini etkinleştirme

Çözümleyici paketleri, güvenlik veya tasarım kuralları gibi bir kural kategorisini etkinleştirmeyi hızlı ve kolay hale getirmek için önceden tanımlanmış [Editorconfig](use-roslyn-analyzers.md#configure-severity-levels) ve/veya [kural kümesi](using-rule-sets-to-group-code-analysis-rules.md) dosyalarını içerebilir. [Microsoft. CodeAnalysis. Netçözümleyiciler](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) NuGet çözümleyici paketi hem editorconfig dosyalarını hem de kural kümelerini içerir. Belirli bir kural kategorisini etkinleştirerek, hedeflenen sorunları ve belirli koşulları belirleyebilirsiniz.

> [!NOTE]
> Visual Studio 2019 sürüm 16,3 ' den başlayarak, çözümleyici kurallarını etkinleştirmek ve bir EditorConfig dosyası kullanarak önem derecesi ayarlamak desteklenir.

Netçözümleyiciler NuGet paketi aşağıdaki kural kategorileri için önceden tanımlanmış EditorConfig dosyalarını ve kural kümelerini içerir:

- Tüm kurallar
- Veri akışı
- Tasarım
- Belgeler
- Genelleştirme
- Birlikte Çalışabilirlik
- Bakım
- Adlandırma
- Performans
- FxCop 'den
- Güvenilirlik
- Güvenlik
- Kullanım

Bu kural kategorilerinin her biri bir EditorConfig veya kural kümesi dosyasına sahiptir:

- Kategorideki tüm kuralları etkinleştir (ve diğer tüm kuralları devre dışı bırak)
- Her kuralın varsayılan önem derecesini kullanın ve varsayılan ayar olarak etkindir (ve diğer tüm kuralları devre dışı bırakın)

> [!TIP]
> "Tüm kurallar" kategorisinin tüm kuralları devre dışı bırakmak için ek bir EditorConfig veya kural kümesi dosyası vardır. Bir projedeki hiçbir çözümleyici uyarılarından veya hatalarından kurtulmak için bu dosyayı kullanın.

> [!TIP]
> Eski "FxCop" analizinden .NET Compiler Platform tabanlı kod çözümlemesine geçiş yapıyorsanız, EditorConfig ve kural kümesi dosyaları, [daha önce kullandığınız](rule-set-reference.md)şekilde benzer kural yapılandırmalarını kullanmaya devam edebilmeniz için izin sağlar.

## <a name="predefined-editorconfig-files"></a>Önceden tanımlanmış EditorConfig dosyaları

Microsoft. CodeAnalysis. Netçözümleyiciler çözümleyici paketinin önceden tanımlanmış EditorConfig dosyaları *% USERPROFILE% \\ . nuget\packages\microsoft.CodeAnalysis.netanalyzers \\ \<version\> \editorconfig* dizininde bulunur. Örneğin, tüm güvenlik kurallarını etkinleştirmek için EditorConfig dosyası *% USERPROFILE% \\ . Nuget\packages\microsoft.CodeAnalysis.netanalyzers \\ \<version\> \Editorconfig\securityrulesenabled \\ . editorconfig*konumunda bulunur.

Seçilen. editorconfig dosyasını projenizin kök dizinine kopyalayın.

## <a name="predefined-rule-sets"></a>Önceden tanımlanmış kural kümeleri

Microsoft. CodeAnalysis. Netçözümleyiciler çözümleyici paketi için önceden tanımlanmış kural kümesi dosyaları *% USERPROFILE% \\ . nuget\packages\microsoft.CodeAnalysis.netanalyzers \\ \<version\> \rulesets* dizininde bulunur. Örneğin, tüm güvenlik kurallarını etkinleştirmek için kural kümesi dosyası *% USERPROFILE% \\ . Nuget\packages\microsoft.CodeAnalysis.netanalyzers \\ \<version\> \Rulesets\securityrulesenabled.exe*konumunda bulunur.

Bir veya daha fazla kural kümesini kopyalayın ve Visual Studio projenizi içeren dizine veya doğrudan **Çözüm Gezgini**yapıştırın.

Ayrıca, [önceden tanımlanmış bir kural kümesini](how-to-create-a-custom-rule-set.md) tercih etmeniz için özelleştirebilirsiniz. Örneğin, bir veya daha fazla kuralın önem derecesini değiştirerek ihlallerin **hata listesi**hata veya uyarı olarak görünmesini sağlayabilirsiniz.


## <a name="rule-scope-options-for-net-code-quality-analyzers"></a>.NET kod kalitesi Çözümleyicileri için kural kapsamı seçenekleri

Bir [Editorconfig dosyasında](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)seçenekleri belirtebilirsiniz. Örneğin, aşağıdaki seçenekleri belirtebilirsiniz.

> [!TIP]
> Kullanılabilir seçeneklerin tam listesini görmek için, bu [çözümleyici Configuration.MD dosyasına](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)bakın. Bir seçeneğin *çözümleyici Configuration.MD* dosyasında nasıl belgelendiği hakkında bir örnek aşağıda verilmiştir:
>
> Seçenek adı: `sufficient_IterationCount_for_weak_KDF_algorithm`\
> Seçenek değerleri: tam sayı değerleri \
> Varsayılan değer: her yapılandırılabilir kurala (' 100000 ' varsayılan olarak çoğu kural için) özeldir \
> Örnek: `dotnet_code_quality.CA5387.sufficient_IterationCount_for_weak_KDF_algorithm = 100000`

## <a name="api_surface"></a>api_surface

| Description | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
| - | - | - | - |
| API yüzeyinin analiz edileceği bölüm | `public`<br/>`internal` veya `friend`<br/>`private`<br/>`all`<br/><br/>Birden çok değeri virgülle ayırın (,) | `public` | [CA1000](ca1000.md) [CA1003](ca1003.md) [CA1008](ca1008.md) [CA1010](ca1010.md)<br/>[CA1012](ca1012.md) [CA1024](ca1024.md) [CA1027](ca1027.md) [CA1028](ca1028.md)<br/>[CA1030](ca1030.md) [CA1036](ca1036.md) [CA1040](ca1040.md) [CA1041](ca1041.md)<br/>[CA1043](ca1043.md) [CA1044](ca1044.md) [CA1051](ca1051.md) [CA1052](ca1052.md)<br/>[CA1054](ca1054.md) [CA1055](ca1055.md) [CA1056](ca1056.md) [CA1058](ca1058.md)<br/>[CA1063](ca1063.md) [CA1708](ca1708.md) [CA1710](ca1710.md) [CA1711](ca1711.md)<br/>[CA1714](ca1714.md) [CA1715](ca1715.md) [CA1716](ca1716.md) [CA1717](ca1717.md)<br/>[CA1720](ca1720.md) [CA1721](ca1721.md) [CA1725](ca1725.md) [CA1801](ca1801.md)<br/>[CA1802](ca1802.md) [CA1815](ca1815.md) [CA1819](ca1819.md) [CA2217](ca2217.md)<br/>[CA2225](ca2225.md) [CA2226](ca2226.md) [CA2231](ca2231.md) [CA2234](ca2234.md)<br/>|

## <a name="exclude_async_void_methods"></a>exclude_async_void_methods

| Description | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
| - | - | - | - |
| Değer döndürmeyen zaman uyumsuz yöntemlerin yoksayılıp yoksayılmayacağı | `true`<br/>`false` | `false` | [CA2007](ca2007.md) |

> [!NOTE]
> 2.6.3 sürümü ve çözümleyici paketinin önceki bölümlerinde, bu seçenek adlandırılmıştı `skip_async_void_methods` .

## <a name="exclude_single_letter_type_parameters"></a>exclude_single_letter_type_parameters

| Description | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
| - | - | - | - |
| Kuraldan tek karakterlik [tür parametrelerinin](/dotnet/csharp/programming-guide/generics/generic-type-parameters) dışlanıp dışlanmayacağı `S` , örneğin `Collection<S>` | `true`<br/>`false` | `false` | [CA1715](ca1715.md) |

> [!NOTE]
> 2.6.3 sürümü ve çözümleyici paketinin önceki bölümlerinde, bu seçenek adlandırılmıştı `allow_single_letter_type_parameters` .

## <a name="output_kind"></a>output_kind

| Description | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
| - | - | - | - |
| Bu tür derlemeyi üreten bir projedeki kodun analiz edilmesi gerektiğini belirtir | Sabit listesinin bir veya daha fazla alanı <xref:Microsoft.CodeAnalysis.OutputKind><br/><br/>Birden çok değeri virgülle ayırın (,) | Tüm çıktı türleri | [CA2007](ca2007.md) |

## <a name="required_modifiers"></a>required_modifiers

| Description | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
| - | - | - | - |
| Çözümlenmesi gereken API 'Ler için gerekli değiştiriciler belirtir | Aşağıdaki izin verilen değiştirici tablosundan bir veya daha fazla değer<br/><br/>Birden çok değeri virgülle ayırın (,) | Her kurala bağlıdır | [CA1802](ca1802.md) |

| İzin verilen değiştirici | Özet |
| --- | --- |
| `none` | Değiştirici gereksinimi yok |
| `static` veya `Shared` | Visual Basic) ' static ' (' Shared ') olarak bildirilmelidir |
| `const` | ' Const ' olarak bildirilmelidir |
| `readonly` | ' ReadOnly ' olarak bildirilmelidir |
| `abstract` | ' Abstract ' olarak bildirilmelidir |
| `virtual` | ' Sanal ' olarak bildirilmelidir |
| `override` | ' Override ' olarak bildirilmelidir |
| `sealed` | ' Sealed ' olarak bildirilmelidir |
| `extern` | ' Extern ' olarak bildirilmelidir |
| `async` | ' Async ' olarak bildirilmelidir |

## <a name="exclude_extension_method_this_parameter"></a>exclude_extension_method_this_parameter

| Description | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
| - | - | - | - |
| Uzantı yöntemlerinin parametresi için analizin atlanıp engellenip engellenmeyeceğini belirtir `this` | `true`<br/>`false` | `false` | [CA1062](ca1062.md) |

## <a name="null_check_validation_methods"></a>null_check_validation_methods

| Description | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
| - | - | - | - |
| Yönteme geçirilen bağımsız değişkenleri doğrulayan null denetim doğrulama yöntemlerinin adları null değil | İzin verilen yöntem adı biçimleri (ile ayrılmış `|` ):<br/> -Yalnızca Yöntem adı (kapsayan tür veya ad alanından bağımsız olarak ada sahip tüm yöntemler dahil)<br/> -Simgenin [belge kimliği biçimindeki](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format), isteğe bağlı bir ön ek olarak nitelenmiş adlar `M:` | Yok | [CA1062](ca1062.md) |

## <a name="additional_string_formatting_methods"></a>additional_string_formatting_methods

| Description | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
| - | - | - | - |
| Ek dize biçimlendirme yöntemlerinin adları | İzin verilen yöntem adı biçimleri (ile ayrılmış `|` ):<br/> -Yalnızca Yöntem adı (kapsayan tür veya ad alanından bağımsız olarak ada sahip tüm yöntemler dahil)<br/> -Simgenin [belge kimliği biçimindeki](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format), isteğe bağlı bir ön ek olarak nitelenmiş adlar `M:` | Yok | [CA2241](ca2241.md) |

## <a name="excluded_type_names_with_derived_types"></a>excluded_type_names_with_derived_types

| Description | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
| - | - | - | - |
| Tür ve türetilmiş tüm türleri analiz için hariç tutulan türlerin adları | İzin verilen sembol adı biçimleri (ile ayrılmış `|` ):<br/> -Yalnızca tür adı (kapsayan tür veya ad alanından bağımsız olarak ada sahip tüm türleri içerir)<br/> -Simgenin [belge kimliği biçimindeki](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format), isteğe bağlı bir ön ek olarak nitelenmiş adlar `T:` | Yok | [CA1303](ca1303.md) |

## <a name="excluded_symbol_names"></a>excluded_symbol_names

| Description | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
| - | - | - | - |
| Analiz için dışlanan simgelerin adları | İzin verilen sembol adı biçimleri (ile ayrılmış `|` ):<br/> -Yalnızca sembol adı (kapsayan tür veya ad alanından bağımsız olarak ada sahip tüm semboller dahil)<br/> -Simgenin [belge kimliği biçiminde](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)tam nitelikli adlar. Her sembol adı, "d:" metotları için önek, "T:" türler için önek, "N:" ad alanları için önek vb. gibi bir sembol türü öneki gerektirir.<br/> - `.ctor` oluşturucular ve `.cctor` statik oluşturucular için | Yok | [CA1062](ca1062.md) [CA1303](ca1303.md) [CA2000](ca2000.md) [CA2100](ca2100.md) [CA2301](ca2301.md) [CA2302](ca2302.md)<br/>[CA2311](ca2311.md) [CA2312](ca2312.md) [CA2321](ca2321.md) [CA2322](ca2322.md) [CA2327](ca2327.md) [CA2328](ca2328.md)<br/>[CA2329](ca2329.md) [CA2330](ca2330.md) [CA3001](ca3001.md) [CA3002](ca3002.md) [CA3003](ca3003.md) [CA3004](ca3004.md)<br/>[CA3005](ca3005.md) [CA3006](ca3006.md) [CA3007](ca3007.md) [CA3008](ca3008.md) [CA3009](ca3009.md) [CA3010](ca3010.md)<br/>[CA3011](ca3011.md) [CA3012](ca3012.md) [CA5361](ca5361.md) CA5376 CA5377 [CA5378](ca5378.md)<br/>[CA5380](ca5380.md) [CA5381](ca5381.md) CA5382 CA5383 CA5384 CA5387<br/>CA5388 [CA5389](ca5389.md) CA5390 |

## <a name="disallowed_symbol_names"></a>disallowed_symbol_names

| Description | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
| - | - | - | - |
| Analiz bağlamında izin verilmeyen simgelerin adları | İzin verilen sembol adı biçimleri (ile ayrılmış `|` ):<br/> -Yalnızca sembol adı (kapsayan tür veya ad alanından bağımsız olarak ada sahip tüm semboller dahil)<br/> -Simgenin [belge kimliği biçiminde](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)tam nitelikli adlar. Her sembol adı, "d:" metotları için önek, "T:" türler için önek, "N:" ad alanları için önek vb. gibi bir sembol türü öneki gerektirir.<br/> - `.ctor` oluşturucular ve `.cctor` statik oluşturucular için | Yok | [CA1031](ca1031.md) |

## <a name="see-also"></a>Ayrıca bkz.

- [Çözümleyici yapılandırması](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [EditorConfig için .NET kodlama kuralları](../ide/editorconfig-code-style-settings-reference.md)
