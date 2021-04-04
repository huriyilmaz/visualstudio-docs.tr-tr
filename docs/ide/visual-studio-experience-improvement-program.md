---
title: Müşteri Deneyimi Geliştirme Programı
description: Visual Studio 'da gizlilik ayarlarını yönetme hakkında bilgi edinin.
ms.date: 05/21/2018
ms.topic: conceptual
author: PoulChapman
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6c7f425d87ba6316c3a3cab66f2b342b4c1141f4
ms.sourcegitcommit: 5c0e20fc6005bc1f8ca38f4122378c4ac21ba89a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2021
ms.locfileid: "106110603"
---
# <a name="visual-studio-customer-experience-improvement-program"></a>Visual Studio Müşteri Deneyimini Geliştirme Programı

Visual Studio Müşteri Deneyimini Geliştirme Programı (VSCEıP), Microsoft 'un zaman içinde Visual Studio 'Yu iyileştirmesine yardımcı olmak için tasarlanmıştır. Bu program hatalar, bilgisayar donanımı ve kişilerin bilgisayardaki görevlerinde kullanıcıları kesintiye uğramadan Visual Studio 'Yu nasıl kullandıkları [hakkında bilgi toplar](../ide/diagnostic-data-collection.md). Toplanan bilgiler Microsoft 'un hangi özellikleri iyileştirebileceğinizi belirlemesine yardımcı olur. Bu belge VSCEıP 'nin nasıl kabul veya dışına alınacağını anlatmaktadır. Bunu devre dışı bırakırsanız, **isteğe bağlı** tanılama veri toplamayı devre dışı olursunuz. Visual Studio 'Nun güvenli olduğundan, güncel olduğundan ve beklendiği gibi çalıştığından emin olmak için bazı tanılama verileri koleksiyonu **gerekir** . Gerekli tanılama veri toplama, VSCEıP 'i devre dışı bırakmak için seçiminizden etkilenmeyecektir.

[!INCLUDE [gdpr-hybrid-note](../misc/includes/gdpr-hybrid-note.md)]
> [!NOTE]
> VSCEıP telemetri kabul etme veya out ayarları, Visual Studio 'da ' sorun bildir ' için uygulanmaz. Bir sorun günlüğü raporlarken, yalnızca ' Gönder ' seçeneğine tıklayarak izin sağladığınızda Microsoft 'a gönderilir. Günlükleri ' bir sorun bildir ' e göndermeden önce yönetmek istiyorsanız lütfen daha fazla ayrıntı için [geri bildirim veri gizliliği](./developer-community-privacy.md) ' ne bakın.

## <a name="opt-in-or-out"></a>Kabul etme veya kapatma

VSCEıP varsayılan olarak açıktır. Bu yönergeleri izleyerek devre dışı bırakabilirsiniz veya tekrar tekrar açabilirsiniz:

1. Visual Studio 'da, **Yardım**  >  **geri bildirimi gönder**' i seçin ve ardından **Ayarlar**' ı seçin.

   **Visual Studio deneyimini geliştirme programı** iletişim kutusu açılır.

1. Devre dışı bırakmak için **Hayır, katılmak istemiyorum**' u seçin ve ardından **Tamam**' ı seçin. Kabul etmek için **Evet, katılmak istiyorum**' u seçin ve ardından **Tamam**' ı seçin.

   ![Visual Studio Deneyimini Geliştirme Programı iletişim kutusu](media/experience-improvement-program.png)

### <a name="registry-settings"></a>Kayıt Defteri ayarları

[Visual Studio Için derleme araçları](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2017)'nı YÜKLERSENIZ, vsceıp 'yi yapılandırmak için kayıt defterini güncelleştirmeniz gerekir. Kurumsal müşteriler, kayıt defteri tabanlı bir ilke ayarlayarak VSCEıP 'i kabul etmek veya kapatmak için bir grup ilkesi oluşturabilir.

İlgili kayıt defteri anahtarı ve ayarları aşağıdaki gibidir:

::: moniker range="vs-2017"

- 64 bitlik bir IŞLETIM sisteminde anahtar = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\15.0\SQM**
- 32 bitlik bir IŞLETIM sisteminde anahtar = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\15.0\SQM**
- Grup ilkesi etkinleştirildiğinde anahtar = **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM**

::: moniker-end

::: moniker range=">=vs-2019"

- 64 bitlik bir IŞLETIM sisteminde anahtar = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\16.0\SQM**
- 32 bitlik bir IŞLETIM sisteminde anahtar = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\16.0\SQM**
- Grup ilkesi etkinleştirildiğinde anahtar = **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM**

::: moniker-end

Entry = **OptIn**

Değer = (DWORD)

- **0** kabul EDILDI (vsceıp 'i kapatın)
- **1** kabul EDILDI (vsceıp 'i açın)

> [!CAUTION]
> Kayıt defterinin hatalı düzenlenmesi sisteminize ciddi şekilde zarar verebilir. Kayıt defterinde değişiklik yapmadan önce, bilgisayarınızdaki tüm değerli verileri yedeklemelisiniz. Ayrıca, el ile yapılan değişiklikler uygulandıktan sonra sorunlarla karşılaşırsanız **bilinen son Iyi yapılandırma** başlatma seçeneğini de kullanabilirsiniz.

VSCEıP tarafından toplanan, işlenen veya aktarılan bilgiler hakkında daha fazla bilgi için [Microsoft gizlilik bildirimi](https://privacy.microsoft.com/privacystatement)' ne bakın.

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio tarafından toplanan tanılama bilgileri](diagnostic-data-collection.md)
* [Visual Studio geri bildirim seçenekleri](../ide/feedback-options.md)
* [Visual Studio ile ilgili sorun bildirme](../ide/how-to-report-a-problem-with-visual-studio.md)
* [Visual Studio Geliştirici topluluğu](https://aka.ms/feedback/suggest?space=8)
* [Microsoft Gizlilik Bildirimi](https://privacy.microsoft.com/privacystatement)
