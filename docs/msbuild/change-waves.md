---
title: Dalgaları değiştirme
description: MSBuild 'de, potansiyel olarak kesintiye uğratan özellikleri etkinleştirmeyi veya devre dışı bırakmayı öğrenin.
ms.date: 11/10/2020
ms.topic: conceptual
helpviewer_keywords:
- Change waves [MSBuild]
- MSBuildDisableFeaturesFromVersion environment variable
author: ghogen
ms.author: ghogen
manager: jmartens
monikerRange: '>=vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 77f93b4741ee987bac871e619ccbe58e2d4d4000
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939532"
---
# <a name="change-waves"></a>Dalgaları değiştirme

*Değişiklik dalgası* , bir ortam değişkeni olarak belirli bir bayrağı belirterek, geri çevirmek Için, MSBuild 'teki bir davranış değişikliği kümesidir. Bunun amacı, bu değişiklikleri standart işlevselliğe dönüşecek şekilde uyarlamak için büyük olasılıkla kesintiye uğratan değişiklikler konusunda sizi uyarır. Belirli bir değişiklik dalgasının tüm özellikleri tek tek değil, birlikte etkinleştirilebilir veya devre dışı bırakılabilir.

MSBuild 'in yeni bir sürümüne yükselttiğinizde, büyük olasılıkla kırılmaya neden olan değişiklikler varsayılan olarak etkindir, ancak bir özellik derlemenizi olumsuz yönde etkiliyorsa, bu değişiklik dalgasını kolayca devre dışı bırakabilirsiniz. Her bir değişiklik dalgası bir MSBuild sürüm numarasıyla tanımlanır (örneğin, 16,8), ancak değişiklik dalgasının ayarlanması, bu MSBuild sürümündeki tüm değişiklikleri değil, derleme işlemini etkileyebilecek belirli özellikleri denetler. [Bu makalenin ilerleyen bölümlerinde](#change-waves-and-associated-features)her değişiklik dalgasının özelliklerinin bir listesi görüntülenir. Değişiklik dalgasının devre dışı bırakılması, daha yüksek sürümlerin değişiklik dalgalarını devre dışı bırakır

## <a name="opt-out-of-change-wave-features"></a>Değişiklik dalga özelliklerini devre dışı

Değişiklik dalgasının özelliklerini devre dışı bırakmak için, ortam değişkenini `MSBuildDisableFeaturesFromVersion` **devre dışı** bırakmak istediğiniz özelliği içeren dalga (veya MSBuild sürümü) olarak ayarlayın. Bu, özelliklerin geliştirildiği MSBuild sürümüdür. Değişiklik dalgalarını aşağıdaki özelliklerle eşleştirmeye bakın.

### <a name="msbuilddisablefeaturesfromversion-values"></a>MSBuildDisableFeaturesFromVersion değerleri

Geçerli bir değişiklik dalgasına ayarlamazsanız, belirli bir dalgaya uyarı ve/veya varsayılan değer gönderilir `MSBuildDisableFeaturesFromVersion` . Aşağıdaki tabloda olası ayarlar gösterilmektedir:

| `MSBuildDisableFeaturesFromVersion` Deeri                         | Sonuç        | Uyarı al mi? |
| :-------------                                                    | :----------   | :----------: |
| Ayarı                                                             | Tüm değişiklik dalgalarını etkinleştirerek her değişiklik dalgasının arkasındaki tüm Özellikler etkinleştirilir.               | Hayır   |
| Geçerli ve geçerli bir değişiklik dalgası (örneğin, `16.8` )                      | Değişiklik dalga `16.8` **ve üstünü** arkasındaki tüm özellikleri devre dışı bırakın.                                           | Hayır   |
| Geçersiz değer (örneğin, `16.9` geçerli dalgalar `16.8` ve ve `16.10` )| Varsayılan değeri en yakın geçerli değer (artan). Örneğin, varsayılan olarak ayarı `16.9` sizin yapmanız gerekir `16.10` .               | Hayır   |
| Döndürme dışı (örneğin, `17.1` en yüksek dalga olduğunda `17.0` )      | En yakın geçerli değere Clamp. Örneğin, `17.1` Clamp 'leri `17.0` ve `16.5` Clamp 'leri `16.8`                    | Yes  |
| Geçersiz biçim (örneğin,, `16x8` , `17_0` `garbage` )                    | Tüm değişiklik dalgalarını etkinleştirerek her değişiklik dalgasının arkasındaki tüm Özellikler etkinleştirilir.               | Yes  |

## <a name="change-waves-and-associated-features"></a>Dalgaları ve ilişkili özellikleri değiştirme

Aşağıdaki listedeki bağlantılar, özelliği için GitHub PR 'ye gider.

### <a name="168"></a>16,8

- [NoWarn 'i etkinleştir](https://github.com/dotnet/msbuild/pull/5671)
- [Hedef/görev atlanan 1024 karakter için günlük iletilerini keser](https://github.com/dotnet/msbuild/pull/5553)
- [Tam sürücü genelleştirmeler yanlış koşulla genişletilmeyin](https://github.com/dotnet/msbuild/pull/5669)

### <a name="1610"></a>16.10

- [Koşuldaki bir özellik genişletmesinin boşluğu olduğunda hata](https://github.com/dotnet/msbuild/pull/5672)

### <a name="170"></a>17.0

Bu değişiklik dalgasına henüz giriş yok.

## <a name="change-waves-that-are-out-of-rotation"></a>Dönüşten olmayan dalgaları değiştirme

Şu anda hiçbir döndürme değişikliği dalgaları yok.

## <a name="faq"></a>SSS

**Değişiklik dalgalarını döndürmek için neden diğer her sürümü hedefleyin?**

Bu sorundan etkilenen ve değişikliklere uyum sağlamak için bu sürenin yeterince zaman olduğuna inandık.

**Neden bir ortam değişkeni, ne bir proje özelliği değil?**

MSBuild projeyi yüklemeden önce bir değişiklik dalga altına bir özellik yerleştirmek istediğimiz senaryolar vardır. Bu nedenle, dalgaları Değiştir ortam değişkenlerini kullanmayı gerektirir.

**Geri alma işlemi neden kabul edilsin?**

Kabul etmek bizim için daha iyi bir yaklaşım, aksi takdirde bir özellik müşteri derlemelerini etkilediği zaman sınırlı geri bildirimde bulunduk.

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild](msbuild.md)
- [MSBuild 16 ' daki yenilikler](whats-new-msbuild-16-0.md)
