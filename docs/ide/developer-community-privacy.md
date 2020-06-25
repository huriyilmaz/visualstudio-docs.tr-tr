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
ms.openlocfilehash: 4f5b8e2d65454d75c08d3efc26af2fd93b22153b
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85284808"
---
# <a name="developer-community-data-privacy"></a>Geliştirici Topluluğu veri gizliliği

Varsayılan olarak, herhangi bir yorum ve yanıt dahil olmak üzere [Geliştirici topluluğu](https://developercommunity.visualstudio.com/)'nda sorunlu tüm bilgiler herkese açık bir şekilde görünür. Tüm topluluğun diğer kullanıcıların bulduğu sorunları, çözümleri ve geçici çözümleri görmesini sağladığından bu faydalıdır. Bununla birlikte, verilerinizin veya kimliğinizin gizliliğiyle ilgili endişeniz varsa seçenekleriniz vardır.

## <a name="identity-privacy"></a>Kimlik gizliliği

Kimliğinizi açığa çıkardıysanız, sizin hakkındaki ayrıntıları açıklamayan [Yeni bir Microsoft hesabı oluşturun](https://signup.live.com/) . Raporunuzu oluşturmak için bu hesabı kullanın.

## <a name="data-privacy"></a>Veri gizliliği

Veri gizliliğiyle ilgilenmeniz durumunda, her zaman genel olan ilk raporun başlığında veya içeriğinde özel tutmak istediğiniz herhangi bir şeyi yerleştirmeyin. Bunun yerine, raporu oluşturun ve ayrı bir açıklamada ayrıntıları özel olarak gönderebileceğinizi unutmayın. Sorun raporu oluşturulduktan sonra, kimlerin yanıt ve ekleri görebileceğini belirtebilirsiniz:

1. Oluşturduğunuz raporda, sorunun özel bir açıklamasını oluşturmak için **Açıklama Ekle** ' yi seçin.

2. Yanıt Düzenleyicisi 'nde Yanıtla ilgili hedef kitlelerinizi belirtmek için **Gönder** ve **iptal** düğmeleri altındaki denetimi kullanın. Microsoft çalışanları ve kendi kendinize yönelik görünürlüğü sınırlamak için **, moderatör ve orijinal poster** seçeneklerini belirleyin.

   ![Geliştirici topluluğu 'nda gizlilik denetimi](media/developer-community-privacy-control.png)

   Yalnızca belirttiğiniz kişiler, yorumu ve içine eklediğiniz tüm görüntüleri, bağlantıları veya kodu görebilir. Yorum altındaki tüm yanıtlar özgün açıklamayla aynı görünürlüğe sahiptir. Yanıtlardaki gizlilik denetimi kısıtlanmış görünürlük durumunu doğru şekilde göstermese de bu durum geçerlidir.

3. Yeniden oluşturma için gereken açıklama ve diğer bilgileri, görüntüleri ve dosya eklerini ekleyin. Bu bilgileri özel olarak göndermek için **Gönder** düğmesini seçin.

   > [!NOTE]
   > Geliştirici topluluğu Web sitesinde, ekli dosyalar ve en fazla 10 dosya için 2 GB 'lik bir sınır vardır. Daha büyük bir dosyayı karşıya yüklemeniz gerekiyorsa, yeni bir sorun raporu gönderebilir veya bir Microsoft çalışanınızdan özel bir yorum için karşıya yükleme URL 'SI isteyebilirsiniz.
   > Bir sorunu kapatdığımızda, ilişkili ekler 90 gün sonra silinir.

Gizliliğinizi korumak ve hassas bilgileri genel görünümden korumak için, Microsoft ile tüm etkileşimleri, görünürlük kısıtlı bir yorum altında yanıt verecek şekilde saklayın. Diğer açıklamalara yanıt vermek, hassas bilgileri yanlışlıkla açıklayabilmeniz için yol açabilir.

## <a name="data-we-collect"></a>Topladığımız veriler

Visual Studio Yükleyicisi **bir sorun bildir** , en son Kurulum günlüğünü topladık.

Visual Studio 'dan **bir sorun rapor** başlatılmışsa, aşağıdaki veri türlerinden bir veya daha fazlasını topladık:

- Watson ve .NET girdileri olay günlüğünden

- Visual Studio bellek içi etkinlik günlüğü dosyası

- Eğer Watson koleksiyonu etkinse PerfWatson dosyaları

- Varsa, Livesuntekler günlük dosyaları

- Varsa Xamarin günlük dosyaları

- Varsa NuGet günlük dosyaları

- Varsa, Web hata ayıklayıcısı günlük dosyaları

- Varsa hizmet merkezi günlükleri ve MEF hata günlükleri

- Varsa Python günlükleri

- Varsa Windows Forms günlükleri

- Bir ekran görüntüsü, eklemeyi tercih ederseniz

- Verileri kaydetme, aşağıdakileri içeren bir kayıt eklemeyi tercih ederseniz:

  - Sorunu yeniden oluşturma adımları

  - ETL izleme dosyası

  - Döküm dosyası

> [!NOTE]
> Kullandığınız günlük dosyaları, ekran görüntüleri ve kayıt verileri, Microsoft 'un kendi özelliklerini anlama ve sorununuzu yanıtlama konusunda önemli ölçüde artış sağlayabilir.  Bu nedenle, bunları dahil etmenizi öneririz. Gizliliğinizi korumak için, ekli günlük dosyaları, ekran görüntüleri ve kayıt verileri yalnızca dahil oldukları sorun raporunu göndererek izin sağladığınızda Microsoft 'a gönderilir. Raporu göndermeden önce ' bir sorun bildir ' penceresinin ' Özet ' adımında hangi dosyaların ekleneceğini görebilirsiniz. ' Özet ' adımında ' sistem günlüklerini Ekle ' seçeneğinin işaretini kaldırarak, sistem günlük dosyalarını rapordan dışlayabilirsiniz. Başvuru için aşağıdaki ekran görüntüsüne bakın. 
  > ![Sorun bildirme-toplanan günlüklerin Özeti](media/report-a-problem-logs-collected.png)


## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio ile ilgili sorun bildirme](how-to-report-a-problem-with-visual-studio.md)
- [C++ sorun raporu veri gizliliği](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset#reports-and-privacy)
