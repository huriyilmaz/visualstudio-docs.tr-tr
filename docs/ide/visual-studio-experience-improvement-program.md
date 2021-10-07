---
title: Müşteri Deneyimi Geliştirme Programı
description: Visual Studio gizlilik ayarlarını yönetme hakkında bilgi edinin.
ms.date: 05/21/2018
ms.topic: conceptual
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 251b440853520bc18e918082cc9607ed2a15ebec
ms.sourcegitcommit: aaa3146356421d921714c29ffd586083570ade3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2021
ms.locfileid: "129635626"
---
# <a name="visual-studio-customer-experience-improvement-program"></a>Visual Studio Müşteri Deneyimini Geliştirme Programı

Visual Studio Müşteri Deneyimini Geliştirme Programı (vsceıp), Microsoft 'un zaman içinde Visual Studio iyileştirilmesine yardımcı olmak için tasarlanmıştır. bu program hatalar, bilgisayar donanımı ve kişilerin bilgisayardaki görevlerinde kullanıcıları kesintiye uğramadan Visual Studio nasıl kullandıkları [hakkında bilgi toplar](../ide/diagnostic-data-collection.md). Toplanan bilgiler Microsoft 'un hangi özellikleri iyileştirebileceğinizi belirlemesine yardımcı olur. Bu belge VSCEıP 'nin nasıl kabul veya dışına alınacağını anlatmaktadır. Bunu devre dışı bırakırsanız, **isteğe bağlı** tanılama veri toplamayı devre dışı olursunuz. Visual Studio güvenli, güncel ve beklendiği gibi gerçekleştirerek emin olmak için bazı tanılama verileri koleksiyonu **gerekir** . Gerekli tanılama veri toplama, VSCEıP 'i devre dışı bırakmak için seçiminizden etkilenmeyecektir.

[!INCLUDE [gdpr-hybrid-note](../misc/includes/gdpr-hybrid-note.md)]
> [!NOTE]
> VSCEıP telemetri kabul etme veya çıkış ayarları, Visual Studio ' bir sorun bildir ' için uygulanmaz. Bir sorun günlüğü raporlarken, yalnızca ' Gönder ' seçeneğine tıklayarak izin sağladığınızda Microsoft 'a gönderilir. Günlükleri ' bir sorun bildir ' e göndermeden önce yönetmek istiyorsanız lütfen daha fazla ayrıntı için [geri bildirim veri gizliliği](./developer-community-privacy.md) ' ne bakın.

## <a name="opt-in-or-out"></a>Kabul etme veya kapatma

VSCEıP varsayılan olarak açıktır. Bu yönergeleri izleyerek devre dışı bırakabilirsiniz veya tekrar tekrar açabilirsiniz:

1. Visual Studio, **yardım**  >  **geri bildirimi gönder**' i ve sonra **Ayarlar**' ı seçin.

   **Visual Studio deneyimi geliştirme programı** iletişim kutusu açılır.

1. Devre dışı bırakmak için **Hayır, katılmak istemiyorum**' u seçin ve ardından **Tamam**' ı seçin. Kabul etmek için **Evet, katılmak istiyorum**' u seçin ve ardından **Tamam**' ı seçin.

   ![Visual Studio Deneyim geliştirme programı iletişim kutusu](media/experience-improvement-program.png)

### <a name="registry-settings"></a>Kayıt Defteri ayarları

[Visual Studio için derleme araçlarını](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2017)yüklerseniz, vsceıp 'yi yapılandırmak için kayıt defterini güncelleştirmeniz gerekir. Enterprise müşteriler, kayıt defteri tabanlı bir ilke ayarlayarak vsceıp 'i kabul etmek veya kapatmak için bir grup ilkesi oluşturabilir.

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
* [Visual Studio sorun bildirme](../ide/how-to-report-a-problem-with-visual-studio.md)
* [Visual Studio Geliştirici Community](https://developercommunity.visualstudio.com/home)
* [Microsoft Gizlilik Bildirimi](https://privacy.microsoft.com/privacystatement)
