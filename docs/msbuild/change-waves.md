---
title: Dalgaları değiştirme
description: Verilerde kesintiye neden olabilecek özellikleri etkinleştirmeyi MSBuild devre dışı bırakmayı öğrenin.
ms.date: 11/10/2020
ms.topic: conceptual
helpviewer_keywords:
- Change waves [MSBuild]
- MSBuildDisableFeaturesFromVersion environment variable
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
monikerRange: '>=vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 30d739c7a0cbdc80a82368128266960e1debca3a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122108986"
---
# <a name="change-waves"></a>Dalgaları değiştirme

Değişiklik *dalgası,* belirli bir bayrak MSBuild ortam değişkeni olarak belirterek devre dışı bırakmanız mümkün olan davranış değişiklikleri kümesidir. Bunun amacı sizi kesintiye neden olabilecek değişiklikler konusunda uyarmaktır, böylece standart işlevlere dönüşmeden önce bu değişikliklere uyum sağlama esnekliğine sahip olursınız. Belirli bir değişiklik dalgasının tüm özellikleri tek tek değil, yalnızca birlikte etkinleştirilebilir veya devre dışı bırakılabilir.

MSBuild'nin yeni bir sürümüne yükseltildiğinde, hataya neden olabilecek değişiklikler varsayılan olarak etkinleştirilir, ancak bir özellik derlemenizi olumsuz etkiliyorsa bu değişiklik dalgasını kolayca devre dışı abilirsiniz. Her değişiklik dalgası bir MSBuild sürüm numarasıyla (örneğin, 16.8) tanımlanır, ancak değişiklik dalgasının ayarı yalnızca derleme sürümündeki tüm değişiklikleri değil, derleme işlemini etkileyebilecek belirli özellikleri MSBuild kontrol eder. Her değişiklik dalgasının özelliklerinin listesi bu [makalenin devamlarında görünür.](#change-waves-and-associated-features) Değişiklik dalgasını devre dışı bırakmak, daha yüksek sürümlerin değişiklik dalgalarını da devre dışı bırakmanızı sağlar.

## <a name="opt-out-of-change-wave-features"></a>Değişiklik dalgası özelliklerini devre dışı bırakma

Bir değişiklik dalgasının özelliklerini devre dışı bırakmak için ortam değişkenlerini devre dışı bırakmak istediğiniz özelliği `MSBuildDisableFeaturesFromVersion` içeren değişiklik dalgasına (veya MSBuild sürümüne) **ayarlayın.** Bu, özelliklerin MSBuild sürümüdür. Değişiklik dalgalarının özelliklerle eşlemesini aşağıda bulabilirsiniz.

### <a name="msbuilddisablefeaturesfromversion-values"></a>MSBuildDisableFeaturesFromVersion Değerleri

Geçerli bir değişiklik dalgasına ayarlanmayacaksa bir uyarı ve/veya varsayılan olarak belirli bir `MSBuildDisableFeaturesFromVersion` dalga alırsınız. Aşağıdaki tabloda olası ayarlar listelemektedir:

| `MSBuildDisableFeaturesFromVersion` Değer                         | Sonuç        | Uyarı mı alasınız? |
| :-------------                                                    | :----------   | :----------: |
| Unset                                                             | Tüm değişiklik dalgalarını etkinleştirin; yani her değişiklik dalgasının arkasındaki tüm özellikler etkinleştirilir.               | Hayır   |
| Geçerli ve geçerli değişiklik dalgası (örneğin, `16.8` )                      | Değişiklik dalgası ve daha yüksek olan tüm özellikleri `16.8` **devre dışı bırakma.**                                           | Hayır   |
| Geçersiz Değer (örneğin, `16.9` geçerli dalgalar ve `16.8` `16.10` olduğunda)| Varsayılan olarak en yakın geçerli değer (artan) değeri kullanılır. Örneğin, ayarı `16.9` varsayılan olarak `16.10` olur.               | Hayır   |
| Döndürme Dışında (örneğin, `17.1` en yüksek dalga `17.0` olduğunda)      | En yakın geçerli değere kadar sıkıştır. Örneğin, `17.1` için sıkıştırmalar `17.0` ve `16.5` için sıkıştırmalar `16.8`                    | Yes  |
| Geçersiz Biçim `16x8` (örneğin, `17_0` , , `garbage` )                    | Tüm değişiklik dalgalarını etkinleştirin; yani her değişiklik dalgasının arkasındaki tüm özellikler etkinleştirilir.               | Yes  |

## <a name="change-waves-and-associated-features"></a>Dalgaları ve ilişkili özellikleri değiştirme

Aşağıdaki listede yer alan bağlantılar, özellik için GitHub PR'ye gider.

### <a name="168"></a>16.8

- [NoWarn'ı etkinleştirme](https://github.com/dotnet/msbuild/pull/5671)
- [Hedef/Görev atlanan günlük iletilerini 1024 karaktere kesme](https://github.com/dotnet/msbuild/pull/5553)
- [Tam sürücü globlarını yanlış koşulla genişletme](https://github.com/dotnet/msbuild/pull/5669)

### <a name="1610"></a>16.10

- [Koşulda özellik genişletmesinde boşluk olduğunda hata oluştu](https://github.com/dotnet/msbuild/pull/5672)

### <a name="170"></a>17.0

Bu değişiklik dalgasına henüz giriş yoktur.

## <a name="change-waves-that-are-out-of-rotation"></a>Dönüş dışında olan dalgaları değiştirme

Şu anda rotasyon dışında değişiklik dalgaları yoktur.

## <a name="faq"></a>SSS

**Neden değişiklik dalgalarını döndürmeye yönelik diğer tüm sürümler hedefli?**

Bu durumdan etkilenenlerle tartışma yapmak ve değişikliklere uyum sağlamak için yeterli zaman olduğuna inanıyoruz.

**Neden proje özelliği değil de ortam değişkeni var?**

Projeyi yükleymeden önce bir özelliği değişiklik dalgasının altına MSBuild senaryolar vardır. Bu nedenle, değişiklik dalgaları ortam değişkenlerini kullanmayı gerektirir.

**Neden kabul etmek yerine geri almayı geri alasınız?**

Geri almayı geri almayı geri almak bizim için daha iyi bir yaklaşımdır, aksi takdirde bir özellik müşterinin derlemelerini etkileyene kadar sınırlı geri bildirim alamayız.

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild](msbuild.md)
- [MSBuild 16'daki yeniler](whats-new-msbuild-16-0.md)
