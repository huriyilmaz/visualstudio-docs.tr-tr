---
title: Sorun raporları için özel veriler
description: Geliştirici raporları için sorun raporları hazırlarken özel verilerinizin daha güvenli Community öğrenin.
ms.custom: SEO-VS-2020
ms.date: 06/21/2018
ms.topic: conceptual
helpviewer_keywords:
- developer community privacy
- privacy, developer community
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 5ecfcbb6cf6e7681bfd68375f1e4b447c23fac83
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049005"
---
# <a name="developer-community-data-privacy"></a>Geliştirici Topluluğu veri gizliliği

Varsayılan olarak, geliştirici raporlarıyla ilgili sorun [raporlarında Community](https://aka.ms/feedback/suggest?space=8)ve yanıtlar da dahil olmak üzere herkes tarafından görülebilir. Topluluğun tamamının diğer kullanıcıların bulduğu sorunları, çözümleri ve geçici çözümleri görmelerini sağlar. Ancak verilerinizin veya kimliğinizin gizliliğiyle ilgili endişeleriniz varsa seçenekleriniz vardır.

## <a name="identity-privacy"></a>Kimlik gizliliği

Kimliğinizi açığa çıkarmakla ilgili endişeleriniz varsa, [Microsoft hesabı](https://signup.live.com/) ifşa Microsoft hesabı yeni bir hesap oluşturun. Raporlarınızı oluşturmak için bu hesabı kullanın.

## <a name="data-privacy"></a>Veri gizliliği

Veri gizliliği konusunda endişeleriniz varsa, gizli tutmak istediğiniz hiçbir şeyi ilk raporun başlığına veya içeriğine (her zaman genel erişime açık) koymayın. Bunun yerine raporu oluşturun ve ayrıntıları ayrı bir açıklamaya özel olarak gönderebilirsiniz. Sorun raporu oluşturulduktan sonra yanıtları ve ekleri kimlerin göreceğini belirtebilirsiniz:

1. Oluşturduğunuz raporda, sorunun özel **açıklamasını oluşturmak** için Açıklama ekle'yi seçin.

2. Yanıt düzenleyicisinde, yanıt hedef kitlesini **belirtmek için Gönder** ve İptal düğmelerinin altındaki denetimi kullanın.  Microsoft **çalışanlarının ve sizin görünürlüğü sınırlamak için Değiştirilebilir** yöneticiler ve özgün posteri seçin.

   ![Geliştirici denetimi üzerinde gizlilik Community](media/developer-community-privacy-control.png)

   Yalnızca sizin belirttiğiniz kişiler açıklamayı ve buna dahil etmek istediğiniz tüm görüntüleri, bağlantıları veya kodu görebilir. Açıklamanın altındaki tüm yanıtlar, özgün açıklamayla aynı görünürlüğüne sahip olur. Yanıtlarda gizlilik denetimi kısıtlanmış görünürlük durumunu doğru göstermese bile bu durum doğrudur.

3. Yeniden projeniz için gereken açıklamayı ve diğer bilgileri, görüntüleri ve dosya eklerini ekleyin. Bu **bilgileri özel** olarak göndermek için Gönder düğmesini seçin.

   > [!NOTE]
   > Developer Community web sitesinde, eklenen dosyalarda 2 GB sınırı ve en fazla 10 dosya vardır. Daha büyük bir dosyayı karşıya yüklemeniz gerekirse yeni bir sorun raporu gönderebilirsiniz veya özel bir açıklamayla Microsoft çalışanlarından karşıya yükleme URL'si isteğinde bulunabilirsiniz.
   > Bir sorunu kapatırken, ilişkili ekler 90 gün sonra silinir.

Gizliliğinizi korumak ve hassas bilgileri genel görünümün dışında tutmak için, Microsoft ile yapılan tüm etkileşimleri, görünürlük kısıtlamalı bir açıklama altında yanıtlar olarak tutmaya dikkat edin. Diğer açıklamalara yanıtlar, hassas bilgileri yanlışlıkla açıklamaya neden olabilir.

## <a name="data-we-collect"></a>Topladığımız veriler

Sorun **bildirme işlemi** bu sorundan Visual Studio Yükleyicisi, en son kurulum günlüğünü toplamız.

Sorun **raporla kaynağından** Visual Studio, aşağıdaki veri türlerinden birini veya daha fazlasını toplarız:

- Olay günlüğünden Watson ve .NET girişleri

- Visual Studio bellek içinde etkinlik günlüğü dosyası

- Watson koleksiyonu etkinse PerfWatson dosyaları

- Varsa LiveShare günlük dosyaları

- Varsa Xamarin günlük dosyaları

- Varsa Nuget günlük dosyaları

- Web hata ayıklayıcısı günlük dosyaları varsa

- Varsa Service Hub günlükleri ve MEF hata günlükleri

- Varsa Python günlükleri

- Razor LSP düzenleyicisi günlükleri varsa

- Windows Varsa form günlükleri

- Dahil etmek istediğiniz ekran görüntüsü

- Aşağıdakileri içeren bir kayıt dahil etmek için veri kaydetme:

  - Sorunu yeniden oluşturma adımları

  - ETL izleme dosyası

  - Döküm dosyası

> [!NOTE]
> Günlük dosyaları, ekran görüntüleri ve gönderilen verileri kaydetme, Microsoft'un sorunlarınızı anlama ve yanıtlama becerisini önemli ölçüde artırabilir.  Bu nedenle bunları dahil öneririz. Gizliliğinizi korumak için tüm ekli günlük dosyaları, ekran görüntüleri ve kayıt verileri yalnızca dahil edildileri sorun raporunu göndererek izinler sağlarken Microsoft'a gönderilir. Raporu göndermeden önce 'Sorun Bildir' penceresinin 'Özet' adımına hangi dosyaların dahil olduğunu görebilirsiniz. 'Özet' adımını 'Sistem günlüklerini ekle' işaretini kaldırarak sistem günlüğü dosyalarını rapordan dışleyebilirsiniz. Başvuru için aşağıdaki ekran görüntüsüne bakın. 
  > ![Sorun Bildirme - Toplanan günlüklerin özeti](media/report-a-problem-logs-collected.png)


## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio ile ilgili bir sorun bildirme](how-to-report-a-problem-with-visual-studio.md)
- [C++ sorun raporu veri gizliliği](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset#reports-and-privacy)
