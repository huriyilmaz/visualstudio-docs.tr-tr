---
title: Bir özellik önerin
description: Geliştirici Hizmetleri'Community, öneride nasıl öneride bulunduruldu ve microsoft tarafından bu yol haritasında önerilerin Visual Studio açıklandı.
ms.date: 10/13/2021
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: d2571174a98c2e8e915239d7f6e1de988788da8d
ms.sourcegitcommit: a8e6a8c6ca36dc76cdc44d1db934eae43470b5fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2021
ms.locfileid: "130030225"
---
# <a name="suggest-a-feature-for-visual-studio"></a>Visual Studio için özellik önerin

Visual Studio Developer Community. ile ilgili sorunları bildirme becerisinin yanı sıra yeni bir özellik önerme [deneyimi Community.](https://aka.ms/feedback/suggest?space=8) Bu, iş akışının mühendislik iş akışıyla doğrudan etkileşim kurmanızı Visual Studio yeni bir yol sağlar.

![Developer Community'da Özellik önerin düğmesi](media/suggest-a-feature/suggest-feature-button.png)

Ayrıca, ana dosya penceresinin sağ Visual Studio  sağ üst köşesindeki Geri Bildirim Sağla simgesinden Öneride Bulunana kadar doğrudan Visual Studio başlatabilirsiniz: 

![Visual Studio'de Bir Öneri menüsü Visual Studio](media/suggest-a-feature/provide-suggestion.png)

**ÖneriDele'nin** seçimi sizi [Geliştirici](https://aka.ms/feedback/suggest?space=8)Community'ye alır ve burada önerinizi girsiniz.

## <a name="suggestion-status"></a>Öneri durumu

Bir özellik önerisi gönderdikten sonra, eyaletler özellik gönderimi yaşam döngüsünde nerede olduğunu gösteriyor. Geri bildiriminizi göz önünde bulundurarak iş akışında taşımaya devam etti olarak ilgili durumla etiketlemektedir. Özellik önerileriyle ilişkili çeşitli eyaletler burada listelenmiştir ve bunların anlamları ve renk göstergelerinin açıklaması yer almaktadır.

- - -
| **Durum** | **Açıklama**                                                                                                         |
|-------------|-------------------------------------------------------------------------------------------------------------------------|
|  ![Geliştirici Hesabı'nın önerileri için yeni Community](../ide/media/SuggestStates/New.jpg)          | **Yeni,** önerinin sizin veya başka bir kişi tarafından yeni bildiriliyor olduğu anlamına gelir. Henüz herhangi bir işlem yapılmadı. Ön satır, devam etmek için bazı ön denetimler yapar. Sonraki adımlarla yaklaşık beş iş günü içinde bizimle bilgi edinebilirsiniz.                    |
|  ![Geliştirici hesabıyla ilgili öneriler için Durumu gözden Community](../ide/media/SuggestStates/UnderReview.jpg)           | **Gözden Geçir'in** altında özellik önerisinin öncelik belirleme için kuyruğa alınana kadar olduğu gösterir. Daha geniş geliştirici topluluğumuza en iyi değeri getirmek için özelliklere öncelik veririz ve ürün yol haritasını da dikkate alacağız. Yeni özellik önerinizi hemen takip emiyor olsak bile yaklaşık 90 gün boyunca fikirlerinizi izlemeye devam edeceğiz, topluluğun da buna ağırlık vermesine ve sonraki adımlarda bir karar vermesine izin vereceksiniz.                    |
|  ![Geliştirici Hesabı önerileri için Yol Haritası Community](../ide/media/SuggestStates/OnRoadmap.jpg)       | **Yol Haritası'nın,** özellik önerinizin geniş bir topluluk etkisine sahip olduğu ve ürün deneyimini geliştirmeye yardımcı olduğu anlamına gelir. Yol haritamızda bunun için zaman ayırdık. İlerleme durumu hakkında sizi güncelleştiriyoruz.                   |
|  ![Geliştirici Hesabı önerileri için Daha Fazla Bilgi durumu Community](../ide/media/SuggestStates/NeedMoreInfo.jpg)          | Daha Fazla Bilgi Gerekiyor **olarak işaretlenmiş bir özellik önerisi,** önerinizi daha iyi anlamamız için daha fazla ayrıntıya ihtiyacımız olduğu anlamına gelir. Daha derin bir anlayış elde etmek için ek bilgi talep edeceğimiz yorumları kontrol edin.                    |
|  ![Kapalı - Geliştirici Hesabı önerileri için diğer ürün Community](../ide/media/SuggestStates/ClosedOtherProduct.jpg)          | **Kapalı - Diğer** Ürün, özellik önerinizi şu anda ele alamayamadığımız anlamına gelir çünkü bu öneri raporlandığı ürün için geçerli değildir. Bununla birlikte, uygun ürün için yeni özellik önerinizi nerede paylaşabilirsiniz hakkında ayrıntılı bilgi sağlarız.                    |
|  ![Kapalı - Geliştirici Hesabı önerileri için yinelenen Community](../ide/media/SuggestStates/ClosedDuplicate.jpg)          | **Kapalı - Yinelenen,** başka birinin zaten aynı özelliği önerdiğini gösterir. Mevcut özellik önerisinin bağlantısını bulmak için yorumları gözden geçirme. Oylar ve yorumlar özgün öneride birleştirilmiştir. Özgün öneriyi izleyin.                    |
|  ![Kapalı - Geliştirici Hesabı önerileri için Yeterli Bilgi Community](../ide/media/SuggestStates/ClosedNotEnoughInfo.jpg)          | **Kapalı - Yeterli Bilgi Yok,** birkaç denemeden sonra özellik önerinizi tam olarak anlamak için yeterli bilgi alamamıştı. Bu aşamada başka bir eylemde yer alamayamadığımız için yeni özellik önerisini kapatmamız gerekiyor. Şu anda aramız olan bilgileri bulduk mu? Ek bilgilere sahipken bileti yeniden etkinleştirmek için istekte bulundurebilirsiniz.                    |
|  ![Kapalı - Geliştirici Hesabı önerileri için Kapsam dışında Community](../ide/media/SuggestStates/closed-out-of-scope.png)           | **Kapalı - Kapsam Dışında** Bir öneri genel ürün yönümüzle eşleşmezse, bunu Kapsam Dışında *olarak kapatırız.* Örneğin, ürün ailesinin diğer üyelerine benzer Visual Studio olabiliriz. Veya önerilen özellik yalnızca birkaç kişi için uygun olabilir ve bu da uzantıyı sağlamak için daha uygun bir uzantı olabilir.                    |
|  ![Tamamlandı - Geliştirici Hesabı önerileri için önizleme Community](../ide/media/SuggestStates/CompletedPreview.jpg)           | **Tamamlandı - Önizleme,** önerdiğimiz özelliği uygulamamız olduğunu gösterir. Yorumlarda sağlanan bağlantıyı kullanarak Visual Studio içeren bir önizleme sürümünü indirebilirsiniz.                    |
|  ![Tamamlandı - Geliştirici Hesabı önerileri için yayın Community](../ide/media/SuggestStates/CompletedRelease.jpg)           | **Tamamlandı - Sürüm,** yeni özellik önerinizin en son ürün güncelleştirmesinde yayımlandı olduğunu gösterir. Bu Visual Studio, açıklamalarda sağlanan bağlantı kullanılarak indirilebilir.                        |

- - -

## <a name="see-also"></a>Ayrıca bkz.

- [Geliştirici Community'da 'Özellik Önerin' tanıtımı (Visual Studio blog)](https://devblogs.microsoft.com/visualstudio/introducing-suggest-a-feature-in-developer-community/?utm_source=vs_developer_news&utm_medium=referral)
