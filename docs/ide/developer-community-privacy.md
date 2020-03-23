---
title: Sorun raporları için özel veriler
ms.date: 06/21/2018
ms.topic: conceptual
helpviewer_keywords:
- developer community privacy
- privacy, developer community
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e87f35778b8aec615410312c0eb7373d4e9969f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75775887"
---
# <a name="developer-community-data-privacy"></a>Geliştirici Topluluğu veri gizliliği

Varsayılan olarak, [geliştirici topluluğuyla](https://developercommunity.visualstudio.com/)ilgili sorun raporlarındaki tüm bilgiler (herhangi bir yorum ve yanıt dahil) genel olarak görülebilir. Bu, tüm topluluğun diğer kullanıcıların bulduğu sorunları, çözümleri ve geçici çözümleri görmesine olanak sağladığı için yararlıdır. Ancak, verilerinizin veya kimliğinizin gizliliği konusunda endişeleriniz varsa, seçenekleriniz vardır.

## <a name="identity-privacy"></a>Kimlik gizliliği

Kimliğinizi ifşa etme konusunda endişeleriniz varsa, sizinle ilgili hiçbir ayrıntıyı açıklamayan [yeni bir Microsoft hesabı oluşturun.](https://signup.live.com/) Raporunuzu oluşturmak için bu hesabı kullanın.

## <a name="data-privacy"></a>Veri gizliliği

Veri gizliliği konusunda endişeleriniz varsa, her zaman herkese açık olan ilk raporun başlığına veya içeriğine gizli tutmak istediğiniz hiçbir şeyi koymayın. Bunun yerine, raporu oluşturun ve ayrıntıları ayrı bir yorumda özel olarak göndereceğinizi unutmayın. Sorun raporu oluşturulduktan sonra, yanıtları ve ekleri kimlerin görebileceğini belirtebilirsiniz:

1. Oluşturduğunuz raporda, sorunun özel bir açıklamasını oluşturmak için **açıklama ekle'yi** seçin.

2. Yanıt düzenleyicisinde, yanıtınızın hedef kitlesini belirtmek için **Gönder** ve **İptal** düğmelerinin altındaki denetimi kullanın. Microsoft çalışanları ve kendinizin görünürlüğünü sınırlamak için **moderatörler tarafından Görüntülenebilir'i ve orijinal posteri** seçin.

   ![Geliştirici Topluluğu'nda gizlilik kontrolü](media/developer-community-privacy-control.png)

   Yalnızca belirttiğiniz kişiler yorumu ve yoruma eklediğiniz resimleri, bağlantıları veya kodu görebilir. Yorumun altındaki yanıtlar, orijinal yorumla aynı görünürlüğe sahiptir. Yanıtlardaki gizlilik denetimi kısıtlanmış görünürlük durumunu doğru şekilde göstermese bile bu durum geçerlidir.

3. Açıklamave repro için gerekli diğer bilgileri, görüntüleri ve dosya eklerini ekleyin. Bu bilgileri özel olarak göndermek için **Gönder** düğmesini seçin.

   > [!NOTE]
   > Ekli dosyalarda 2 GB sınırı ve en fazla 10 dosya vardır. Daha büyük bir dosya yüklemeniz gerekiyorsa, yeni bir sorun raporu gönderebilir veya özel bir yorumda bir Microsoft çalışanından yükleme URL'si isteyebilirsiniz.

Gizliliğinizi korumak ve hassas bilgileri genel görünümden uzak tutmak için, microsoft ile tüm etkileşimleri görünürlük kısıtlamalı bir yorum altında yanıtlara karşı tutmaya özen deyin. Diğer yorumlara verilen yanıtlar, hassas bilgileri yanlışlıkla ifşa etmenize neden olabilir.

## <a name="data-we-collect"></a>Topladığımız veriler

Visual Studio Installer'dan **bir sorun bildir** başlatılırsa, en son kurulum günlüğünü toplarız.

Visual Studio'dan **bir sorun bildir** başlatılırsa, aşağıdaki veri türlerinden birini veya birkaçını toplarız:

- Etkinlik günlüğünden Watson ve .NET girişleri

- Visual Studio bellek içi etkinlik günlüğü dosyası

- Watson koleksiyonu etkinse, PerfWatson dosyaları

- LiveShare günlük dosyaları varsa

- Xamarin günlük dosyaları, varsa

- Nuget günlük dosyaları varsa,

- Varsa Web hata ayıklama günlük dosyaları

- Varsa Servis Hub günlükleri ve MEF hata günlükleri

- Python günlükleri, varsa

- Windows Forms günlükleri varsa

- Eklemeyi seçerseniz bir ekran görüntüsü

- Aşağıdakileri içeren bir kayıt eklemeyi seçerseniz, veri kaydetme:

  - Sorunu yeniden oluşturma adımları

  - ETL izleme dosyası

  - Dosyayı boşaltın

> [!NOTE]
> Günlük dosyaları, ekran görüntüleri ve gönderdiğiniz verileri kaydetmek Microsoft'un sorununuzu anlama ve yanıtverme yeteneğini önemli ölçüde artırabilir.  Bu yüzden onları da dahil öneririz. Gizliliğinizi korumak için, ekli günlük dosyaları, ekran görüntüleri ve kayıt verileri yalnızca dahil oldukları sorun raporunu göndererek izin verdiğinizde Microsoft'a gönderilir. Raporu göndermeden önce 'Sorun Bildir' penceresinin 'Özet' adımında hangi dosyaların yer aldığınızı görebilirsiniz. 'Özet' adımında 'Sistem günlüklerini ekle' işaretlerini uncheck'i açarak sistem günlüğü dosyalarını rapordan çıkarabilirsiniz. Başvuru için aşağıdaki ekran görüntüsüne bakın. 
  > ![Sorun Bildir - Toplanan günlüklerin özeti](media/report-a-problem-logs-collected.png)


## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio ile ilgili bir sorun nasıl bildirilir?](how-to-report-a-problem-with-visual-studio.md)
- [C++ sorun raporu veri gizliliği](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset#reports-and-privacy)
