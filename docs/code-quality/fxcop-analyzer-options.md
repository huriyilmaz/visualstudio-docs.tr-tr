---
title: FxCop Çözümleyicisi yapılandırma seçenekleri
ms.date: 09/23/2019
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 7d6b56bec2174ca71cc66f5424b7bdc309330d95
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2020
ms.locfileid: "88248794"
---
# <a name="rule-scope-options-for-fxcop-analyzers"></a>FxCop çözümleyicileri için kural kapsamı seçenekleri

Bazı FxCop çözümleyici kuralları, kod tabanınızın hangi bölümlerinin uygulanacağını iyileştirmenize olanak tanır. Bu sayfada kullanılabilir kapsam yapılandırma seçenekleri, izin verilen değerler ve uygulandıkları kurallar listelenir. Bu seçenekleri kullanmak için bunları bir [Editorconfig dosyasında](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)belirtin.

Bu yapılandırma seçenekleri [Microsoft. CodeAnalysis. Fxcopçözümleyiciler](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet paketinin 2.6.3 sürümünden başlayarak kullanılabilir.

> [!TIP]
> Fxcopçözümleyiciler paketinin belirli bir sürümü için kullanılabilen seçeneklerin tam listesini görmek için, paketin *Belgeler* klasöründeki *Analyzer Configuration.MD* dosyasına bakın. Dosya *% USERPROFILE% \\ . Nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers \\ \<version\> \Belgetation\analyzer Configuration.MD*konumunda bulunur. Bu yapılandırma belge dosyası, sürüm 2.6.5 'den başlayarak paketin her bir sürümüne dahildir. Bir seçeneğin *çözümleyici Configuration.MD* dosyasında nasıl belgelendiği hakkında bir örnek aşağıda verilmiştir:
>
> Seçenek adı: `sufficient_IterationCount_for_weak_KDF_algorithm`\
> Seçenek değerleri: tam sayı değerleri \
> Varsayılan değer: her yapılandırılabilir kurala (' 100000 ' varsayılan olarak çoğu kural için) özeldir \
> Örnek: `dotnet_code_quality.CA5387.sufficient_IterationCount_for_weak_KDF_algorithm = 100000`

## <a name="api_surface"></a>api_surface

| Açıklama | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
| - | - | - | - |
| API yüzeyinin analiz edileceği bölüm | `public`<br/>`internal` veya `friend`<br/>`private`<br/>`all`<br/><br/>Birden çok değeri virgülle ayırın (,) | `public` | [CA1000](ca1000.md) [CA1003](ca1003.md) [CA1008](ca1008.md) [CA1010](ca1010.md)<br/>[CA1012](ca1012.md) [CA1024](ca1024.md) [CA1027](ca1027.md) [CA1028](ca1028.md)<br/>[CA1030](ca1030.md) [CA1036](ca1036.md) [CA1040](ca1040.md) [CA1041](ca1041.md)<br/>[CA1043](ca1043.md) [CA1044](ca1044.md) [CA1051](ca1051.md) [CA1052](ca1052.md)<br/>[CA1054](ca1054.md) [CA1055](ca1055.md) [CA1056](ca1056.md) [CA1058](ca1058.md)<br/>[CA1063](ca1063.md) [CA1708](ca1708.md) [CA1710](ca1710.md) [CA1711](ca1711.md)<br/>[CA1714](ca1714.md) [CA1715](ca1715.md) [CA1716](ca1716.md) [CA1717](ca1717.md)<br/>[CA1720](ca1720.md) [CA1721](ca1721.md) [CA1725](ca1725.md) [CA1801](ca1801.md)<br/>[CA1802](ca1802.md) [CA1815](ca1815.md) [CA1819](ca1819.md) [CA2217](ca2217.md)<br/>[CA2225](ca2225.md) [CA2226](ca2226.md) [CA2231](ca2231.md) [CA2234](ca2234.md)<br/>|

## <a name="exclude_async_void_methods"></a>exclude_async_void_methods

| Açıklama | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
| - | - | - | - |
| Değer döndürmeyen zaman uyumsuz yöntemlerin yoksayılıp yoksayılmayacağı | `true`<br/>`false` | `false` | [CA2007](ca2007.md) |

> [!NOTE]
> 2.6.3 sürümü ve çözümleyici paketinin önceki bölümlerinde, bu seçenek adlandırılmıştı `skip_async_void_methods` .

## <a name="exclude_single_letter_type_parameters"></a>exclude_single_letter_type_parameters

| Açıklama | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
| - | - | - | - |
| Kuraldan tek karakterlik [tür parametrelerinin](/dotnet/csharp/programming-guide/generics/generic-type-parameters) dışlanıp dışlanmayacağı `S` , örneğin `Collection<S>` | `true`<br/>`false` | `false` | [CA1715](ca1715.md) |

> [!NOTE]
> 2.6.3 sürümü ve çözümleyici paketinin önceki bölümlerinde, bu seçenek adlandırılmıştı `allow_single_letter_type_parameters` .

## <a name="output_kind"></a>output_kind

| Açıklama | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
| - | - | - | - |
| Bu tür derlemeyi üreten bir projedeki kodun analiz edilmesi gerektiğini belirtir | Sabit listesinin bir veya daha fazla alanı <xref:Microsoft.CodeAnalysis.OutputKind><br/><br/>Birden çok değeri virgülle ayırın (,) | Tüm çıktı türleri | [CA2007](ca2007.md) |

## <a name="required_modifiers"></a>required_modifiers

| Açıklama | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
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

| Açıklama | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
| - | - | - | - |
| Uzantı yöntemlerinin parametresi için analizin atlanıp engellenip engellenmeyeceğini belirtir `this` | `true`<br/>`false` | `false` | [CA1062](ca1062.md) |

## <a name="null_check_validation_methods"></a>null_check_validation_methods

| Açıklama | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
| - | - | - | - |
| Yönteme geçirilen bağımsız değişkenleri doğrulayan null denetim doğrulama yöntemlerinin adları null değil | İzin verilen yöntem adı biçimleri (ile ayrılmış `|` ):<br/> -Yalnızca Yöntem adı (kapsayan tür veya ad alanından bağımsız olarak ada sahip tüm yöntemler dahil)<br/> -Simgenin [belge kimliği biçimindeki](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format), isteğe bağlı bir ön ek olarak nitelenmiş adlar `M:` | Yok | [CA1062](ca1062.md) |

## <a name="additional_string_formatting_methods"></a>additional_string_formatting_methods

| Açıklama | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
| - | - | - | - |
| Ek dize biçimlendirme yöntemlerinin adları | İzin verilen yöntem adı biçimleri (ile ayrılmış `|` ):<br/> -Yalnızca Yöntem adı (kapsayan tür veya ad alanından bağımsız olarak ada sahip tüm yöntemler dahil)<br/> -Simgenin [belge kimliği biçimindeki](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format), isteğe bağlı bir ön ek olarak nitelenmiş adlar `M:` | Yok | [CA2241](ca2241.md) |

## <a name="excluded_type_names_with_derived_types"></a>excluded_type_names_with_derived_types

| Açıklama | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
| - | - | - | - |
| Tür ve türetilmiş tüm türleri analiz için hariç tutulan türlerin adları | İzin verilen sembol adı biçimleri (ile ayrılmış `|` ):<br/> -Yalnızca tür adı (kapsayan tür veya ad alanından bağımsız olarak ada sahip tüm türleri içerir)<br/> -Simgenin [belge kimliği biçimindeki](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format), isteğe bağlı bir ön ek olarak nitelenmiş adlar `T:` | Yok | [CA1303](ca1303.md) |

## <a name="excluded_symbol_names"></a>excluded_symbol_names

| Açıklama | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
| - | - | - | - |
| Analiz için dışlanan simgelerin adları | İzin verilen sembol adı biçimleri (ile ayrılmış `|` ):<br/> -Yalnızca sembol adı (kapsayan tür veya ad alanından bağımsız olarak ada sahip tüm semboller dahil)<br/> -Simgenin [belge kimliği biçiminde](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)tam nitelikli adlar. Her sembol adı, "d:" metotları için önek, "T:" türler için önek, "N:" ad alanları için önek vb. gibi bir sembol türü öneki gerektirir.<br/> - `.ctor` oluşturucular ve `.cctor` statik oluşturucular için | Yok | [CA1062](ca1062.md) [CA1303](ca1303.md) [CA2000](ca2000.md) [CA2100](ca2100.md) [CA2301](ca2301.md) [CA2302](ca2302.md)<br/>[CA2311](ca2311.md) [CA2312](ca2312.md) [CA2321](ca2321.md) [CA2322](ca2322.md) [CA2327](ca2327.md) [CA2328](ca2328.md)<br/>[CA2329](ca2329.md) [CA2330](ca2330.md) [CA3001](ca3001.md) [CA3002](ca3002.md) [CA3003](ca3003.md) [CA3004](ca3004.md)<br/>[CA3005](ca3005.md) [CA3006](ca3006.md) [CA3007](ca3007.md) [CA3008](ca3008.md) [CA3009](ca3009.md) [CA3010](ca3010.md)<br/>[CA3011](ca3011.md) [CA3012](ca3012.md) [CA5361](ca5361.md) CA5376 CA5377 [CA5378](ca5378.md)<br/>[CA5380](ca5380.md) [CA5381](ca5381.md) CA5382 CA5383 CA5384 CA5387<br/>CA5388 [CA5389](ca5389.md) CA5390 |

## <a name="disallowed_symbol_names"></a>disallowed_symbol_names

| Açıklama | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
| - | - | - | - |
| Analiz bağlamında izin verilmeyen simgelerin adları | İzin verilen sembol adı biçimleri (ile ayrılmış `|` ):<br/> -Yalnızca sembol adı (kapsayan tür veya ad alanından bağımsız olarak ada sahip tüm semboller dahil)<br/> -Simgenin [belge kimliği biçiminde](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)tam nitelikli adlar. Her sembol adı, "d:" metotları için önek, "T:" türler için önek, "N:" ad alanları için önek vb. gibi bir sembol türü öneki gerektirir.<br/> - `.ctor` oluşturucular ve `.cctor` statik oluşturucular için | Yok | [CA1031](ca1031.md) |
