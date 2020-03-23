---
title: Müşteri Deneyimi Geliştirme Programı
description: Visual Studio'da gizlilik ayarlarını nasıl yönetabileceğinizi öğrenin.
ms.date: 05/21/2018
ms.topic: conceptual
author: PoulChapman
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b6c785b755b64f0dd7e367a01d9c05c1981ea558
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "71693009"
---
# <a name="visual-studio-customer-experience-improvement-program"></a>Visual Studio Müşteri Deneyimini Geliştirme Programı

Visual Studio Müşteri Deneyimi Geliştirme Programı (VSCEIP), Microsoft'un Visual Studio'yu zaman içinde geliştirmesine yardımcı olmak için tasarlanmıştır. Bu [program, bilgisayardaki](../ide/diagnostic-data-collection.md)görevlerinde kullanıcıları kesintiye uğratmadan hatalar, bilgisayar donanımı ve insanların Visual Studio'yu nasıl kullandıkları hakkında bilgi toplar. Toplanan bilgiler, Microsoft'un hangi özelliklerin geliştireceğini belirlemesine yardımcı olur. Bu belge, VSCEIP'e nasıl seçilen veya devre dışı kolunmayı kapsar.

[!INCLUDE [gdpr-hybrid-note](../misc/includes/gdpr-hybrid-note.md)]
> [!NOTE]
> VSCEIP telemetri seve meslerken veya devre dışı bırakma ayarları Visual Studio'daki 'Sorunu Bildir' için geçerli değildir. Bir sorun günlükleri rapor ettiğinizde toplanır ve Microsoft'a gönderilir yalnızca 'Gönder'i tıklayarak izin verdiğinizde. 'Bir Sorunu Bildir' adresine göndermeden önce günlükleri yönetmek istiyorsanız, daha fazla bilgi için lütfen [Geri Bildirim Veri Gizliliği'ne](./developer-community-privacy.md) bakın.

## <a name="opt-in-or-out"></a>Devre dışı bırakma veya çıkarma

VSCEIP varsayılan olarak açık. Aşağıdaki yönergeleri izleyerek kapatabilir veya yeniden açabilirsiniz:

1. Visual Studio'da Geri Bildirim **Gönder'i** > **Send Feedback**seçin ve ardından **Ayarlar'ı**seçin.

   **Visual Studio Deneyim Geliştirme Programı** iletişim kutusu açılır.

1. Devre dışı bırakmak için, **Hayır'ı seçin, katılmak istiyorum**ve sonra **Tamam'ı**seçin. Katılmak için **Evet'i seçin, katılmaya hazırım**ve sonra **Tamam'ı**seçin.

   ![Visual Studio Deneyim Geliştirme Programı iletişim](media/experience-improvement-program.png)

### <a name="registry-settings"></a>Kayıt defteri ayarları

Visual Studio [için Yapı Araçları'nı](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2017)yüklerseniz, VSCEIP'i yapılandırmak için kayıt defterini güncelleştirmeniz gerekir. Kurumsal müşteriler, kayıt defteritabanlı bir ilke ayarlayarak VSCEIP'e kabul etmek veya devre dışı bırakmak için bir grup ilkesi oluşturabilirsiniz.

İlgili kayıt defteri anahtarı ve ayarları aşağıdaki gibidir:

::: moniker range="vs-2017"

- 64 bit işletim sistemi üzerinde, Anahtar = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Düğüm\Microsoft\VSCommon\15.0\SQM**
- 32 bit işletim sistemi üzerinde Anahtar = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\15.0\SQM**
- Grup İlkesi etkinleştirildiğinde, Anahtar = **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM**

::: moniker-end

::: moniker range=">=vs-2019"

- 64 bit işletim sistemi üzerinde, Anahtar = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Düğüm\Microsoft\VSCommon\16.0\SQM**
- 32 bit işletim sistemi üzerinde Anahtar = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\16.0\SQM**
- Grup İlkesi etkinleştirildiğinde, Anahtar = **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM**

::: moniker-end

Giriş = **Optin**

Değer = (DWORD)

- **0** devre dışı bırakılır (VSCEIP kapatın)
- **1** tercih edilir (VSCEIP'i açın)

> [!CAUTION]
> Kayıt defterinin hatalı düzenlenmesi sisteminize ciddi şekilde zarar verebilir. Kayıt defterinde değişiklik yapmadan önce, bilgisayarınızdaki tüm değerli verileri yedeklemelisiniz. El ile değişiklikler uygulandıktan sonra sorunlarla **karşılaşırsanız, Bilinen Son Bilinen İyi Yapılandırma** başlatma seçeneğini de kullanabilirsiniz.

VSCEIP tarafından toplanan, işlenen veya iletilen bilgiler hakkında daha fazla bilgi için [Microsoft Gizlilik Bildirimi'ne](https://privacy.microsoft.com/privacystatement)bakın.

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio tarafından toplanan tanısal bilgiler](diagnostic-data-collection.md)
* [Visual Studio geri bildirim seçenekleri](../ide/feedback-options.md)
* [Visual Studio ile ilgili bir sorun nasıl bildirilir?](../ide/how-to-report-a-problem-with-visual-studio.md)
* [Visual Studio Geliştirici Topluluğu](https://developercommunity.visualstudio.com/)
* [Microsoft Gizlilik Bildirimi](https://privacy.microsoft.com/privacystatement)
