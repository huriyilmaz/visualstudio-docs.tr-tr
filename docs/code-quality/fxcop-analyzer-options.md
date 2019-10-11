---
title: FxCop Çözümleyicisi yapılandırma seçenekleri
ms.date: 09/23/2019
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c6eb32357998f0867b00a5ef0e9119c3c357ed1b
ms.sourcegitcommit: b23d73c86ec7720c4cd9a58050860bc559623a3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72172739"
---
# <a name="rule-scope-options-for-fxcop-analyzers"></a>FxCop çözümleyicileri için kural kapsamı seçenekleri

Bazı FxCop çözümleyici kuralları, kod tabanınızın hangi bölümlerinin uygulanacağını iyileştirmenize olanak tanır. Bu sayfada kullanılabilir kapsam yapılandırma seçenekleri, izin verilen değerler ve uygulandıkları kurallar listelenir. Bu seçenekleri kullanmak için bunları bir [Editorconfig dosyasında](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)belirtin.

Bu yapılandırma seçenekleri [Microsoft. CodeAnalysis. Fxcopçözümleyiciler](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet paketinin 2.6.3 sürümünden başlayarak kullanılabilir.

> [!TIP]
> Fxcopçözümleyiciler paketinin belirli bir sürümü için kullanılabilen seçeneklerin tam listesini görmek için, paketin *Belgeler* klasöründeki *Analyzer Configuration.MD* dosyasına bakın. Dosya *% USERPROFILE% \\. nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers @ no__t-2 @ no__t-3version @ no__t-4\documentation\Analyzer Configuration.MD*konumunda bulunuyor. Bu yapılandırma belge dosyası, sürüm 2.6.5 'den başlayarak paketin her bir sürümüne dahildir. Bir seçeneğin *çözümleyici Configuration.MD* dosyasında nasıl belgelendiği hakkında bir örnek aşağıda verilmiştir:
>
> Seçenek adı: `sufficient_IterationCount_for_weak_KDF_algorithm` @ no__t-1
> Seçenek değerleri: tam sayı değerleri \
> Varsayılan değer: Her yapılandırılabilir kurala (' 100000 ' varsayılan olarak çoğu kural için) özeldir \
> Örnek: `dotnet_code_quality.CA5387.sufficient_IterationCount_for_weak_KDF_algorithm = 100000`

## <a name="api_surface"></a>api_surface

| Açıklama | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
| - | - | - | - |
| API yüzeyinin analiz edileceği bölüm | `public`<br/>`internal` veya `friend`<br/>`private`<br/>`all`<br/><br/>Birden çok değeri virgülle ayırın (,) | `public` | [CA1000](ca1000-do-not-declare-static-members-on-generic-types.md)<br/>[CA1003](ca1003-use-generic-event-handler-instances.md)<br/>[CA1008](ca1008-enums-should-have-zero-value.md)<br/>[CA1010](ca1010-collections-should-implement-generic-interface.md)<br/>[CA1012](ca1012-abstract-types-should-not-have-constructors.md)<br/>[CA1024](ca1024-use-properties-where-appropriate.md)<br/>[CA1027](ca1027-mark-enums-with-flagsattribute.md)<br/>[CA1028](ca1028-enum-storage-should-be-int32.md)<br/>[CA1030](ca1030-use-events-where-appropriate.md)<br/>[CA1036](ca1036-override-methods-on-comparable-types.md)<br/>[CA1040](ca1040-avoid-empty-interfaces.md)<br/>[CA1041](ca1041-provide-obsoleteattribute-message.md)<br/>[CA1043](ca1043-use-integral-or-string-argument-for-indexers.md)<br/>[CA1044](ca1044-properties-should-not-be-write-only.md)<br/>[CA1051](ca1051-do-not-declare-visible-instance-fields.md)<br/>[CA1052](ca1052-static-holder-types-should-be-sealed.md)<br/>[CA1054](ca1054-uri-parameters-should-not-be-strings.md)<br/>[CA1055](ca1055-uri-return-values-should-not-be-strings.md)<br/>[CA1056](ca1056-uri-properties-should-not-be-strings.md)<br/>[CA1058](ca1058-types-should-not-extend-certain-base-types.md)<br/>[CA1063](ca1063-implement-idisposable-correctly.md)<br/>[CA1708](ca1708-identifiers-should-differ-by-more-than-case.md)<br/>[CA1710](ca1710-identifiers-should-have-correct-suffix.md)<br/>[CA1711](ca1711-identifiers-should-not-have-incorrect-suffix.md)<br/>[CA1714](ca1714-flags-enums-should-have-plural-names.md)<br/>[CA1715](ca1715-identifiers-should-have-correct-prefix.md)<br/>[CA1716](ca1716-identifiers-should-not-match-keywords.md)<br/>[CA1717](ca1717-only-flagsattribute-enums-should-have-plural-names.md)<br/>[CA1720](ca1720-identifiers-should-not-contain-type-names.md)<br/>[CA1721](ca1721-property-names-should-not-match-get-methods.md)<br/>[CA1725](ca1725-parameter-names-should-match-base-declaration.md)<br/>[CA1802](ca1802-use-literals-where-appropriate.md)<br/>[CA1815](ca1815-override-equals-and-operator-equals-on-value-types.md)<br/>[CA1819](ca1819-properties-should-not-return-arrays.md)<br/>[CA2217](ca2217-do-not-mark-enums-with-flagsattribute.md)<br/>[CA2225](ca2225-operator-overloads-have-named-alternates.md)<br/>[CA2226](ca2226-operators-should-have-symmetrical-overloads.md)<br/>[CA2231](ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)<br/>[CA2234](ca2234-pass-system-uri-objects-instead-of-strings.md) |

## <a name="exclude_async_void_methods"></a>exclude_async_void_methods

| Açıklama | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
| - | - | - | - |
| Değer döndürmeyen zaman uyumsuz yöntemlerin yoksayılıp yoksayılmayacağı | `true`<br/>`false` | `false` | [CA2007](ca2007-do-not-directly-await-task.md) |

> [!NOTE]
> 2\.6.3 sürümü ve çözümleyici paketinin önceki bölümlerinde, bu seçenek `skip_async_void_methods` olarak adlandırılmıştır.

## <a name="exclude_single_letter_type_parameters"></a>exclude_single_letter_type_parameters

| Açıklama | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
| - | - | - | - |
| Kuraldan tek karakterlik [tür parametrelerinin](/dotnet/csharp/programming-guide/generics/generic-type-parameters) dışarıda bırakılıp bırakılmayacağını belirtir, örneğin, `Collection<S>` içinde `S` | `true`<br/>`false` | `false` | [CA1715](ca1715-identifiers-should-have-correct-prefix.md) |

> [!NOTE]
> 2\.6.3 sürümü ve çözümleyici paketinin önceki bölümlerinde, bu seçenek `allow_single_letter_type_parameters` olarak adlandırılmıştır.

## <a name="output_kind"></a>output_kind

| Açıklama | İzin verilen değerler | Varsayılan değer | Yapılandırılabilir kurallar |
| - | - | - | - |
| Bu tür derlemeyi üreten bir projedeki kodun analiz edilmesi gerektiğini belirtir | @No__t-0 sabit listesinin bir veya daha fazla alanı<br/><br/>Birden çok değeri virgülle ayırın (,) | Tüm çıktı türleri | [CA2007](ca2007-do-not-directly-await-task.md) |