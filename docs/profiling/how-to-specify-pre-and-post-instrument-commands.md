---
title: 'Nasıl Yapılır: Ön ve Post-Enstrüman Komutlarını Belirt | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.instrument
helpviewer_keywords:
- profiling tools, pre-instrument events
- events [Visual Studio], pre-instrument
- pre-instrument events, performance tools
ms.assetid: 6a8d5340-1d1b-4d81-88dd-8e1f435eb828
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 22ad5558ed01e5bb1b8d12b7a4cc65b4d677d0cd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778719"
---
# <a name="how-to-specify-pre--and-post-instrument-commands"></a>Nasıl yapılır: Enstrüman öncesi ve sonrası komutları belirtin

Performans oturumundaki ikililerden önce veya sonra çalışan komutları belirtebilirsiniz. Komut satırından verilebilecek herhangi bir komut bir ön enstrüman veya bir enstrüman sonrası olay olarak belirtilebilir. Örneğin, ikili araçlar enstrümante edildikten sonra yürütülen toplu iş dosyasında güçlü bir ad anahtarıyla bir derlemenin istifasını otomatikleştiren komutlar belirtebilirsiniz.

Profil oluşturma çalışmasındaki tüm enstrümantasyonlu ikililer veya tek tek ikililer için komutlar belirtebilirsiniz. Ancak, önce çalıştırmak için yalnızca bir ön enstrüman komutu ve enstrümantasyon işleminden sonra çalıştırmak için yalnızca bir post-enstrüman komutu belirtebilirsiniz. Hem tüm ikililer hem de tek tek ikililer için komutlar belirtemezsiniz. Tüm ikililer için komutları belirttiğiniz zaman, komutlar oturumdaki her ikilinin enstrümantasyonundan önce veya sonra çalıştırılır.

Komutların yürütüldüğü çalışma dizini, çalıştığınız [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] işletim sistemine ve profilli uygulamanın hedef platformuna bağlıdır.

Profil oluşturma araçlarına giden yolu almak [için](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)bkz.

## <a name="to-specify-pre-instrument-commands"></a>Ön enstrüman komutlarını belirtmek için

1. Aşağıdaki adımlardan birini uygulayın:

    - Performans oturumundaki tüm ikililer için ön enstrüman komutları belirtmek **için, Performans Gezgini'ndeki**performans oturumu düğümünü seçin ve ardından Sağ tıklatın ve **Özellikler'i**seçin.

    - Belirli bir ikili için ön enstrüman komutları belirtmek için, performans oturumunun **Hedefler** listesinde ikilinin adını sağ tıklatın ve ardından **Özellikler'i**seçin.

2. Özellik **Sayfalarında**, **Enstrümantasyon'u**tıklatın.

3. Komut **satırı** metin kutusuna **Ön Enstrüman olaylarının**altına komutu yazın.

    > [!NOTE]
    > Komut **satırı** kutusuna göz atmak ve uygun .exe, .cmd veya .bat dosyasını seçmek için bitişik olan elips düğmesini **(...)** tıklatabilirsiniz.

4. **Tamam**'a tıklayın.

     Komutu çıkarmadan çalışmasını engellemek için **enstrümantasyon onay kutusundan Dışla'yı** seçin. Derleyici veya bağlayıcı ayarlarını değiştirmek için proje özelliği sayfalarını kullanın.

## <a name="to-specify-post-instrument-commands"></a>Enstrüman sonrası komutları belirtmek için

1. Aşağıdaki adımlardan birini uygulayın:

    - Performans oturumundaki tüm ikililer için enstrüman sonrası komutları belirtmek **için, Performans Gezgini'ndeki**performans oturumu düğümünü seçin ve ardından Sağ tıklatın ve **Özellikler'i**seçin.

    - Belirli bir ikili için enstrüman sonrası komutları belirtmek için, performans oturumunun **Hedefler** listesinde ikilinin adını sağ tıklatın ve ardından **Özellikler'i**seçin.

2. Özellik **Sayfalarında**, **Enstrümantasyon'u**tıklatın.

3. **Post-Instrument olayları**altında **Komut satırı** metin kutusuna komutu yazın.

    > [!NOTE]
    > Komut **satırı** kutusuna göz atmak ve uygun .exe, .cmd veya .bat dosyasını seçmek için bitişik olan elips düğmesini **(...)** tıklatabilirsiniz.

4. **Tamam**'a tıklayın.

     Komutu çıkarmadan çalışmasını engellemek için **enstrümantasyon onay kutusundan Dışla'yı** seçin. Derleyici veya bağlayıcı ayarlarını değiştirmek için proje özelliği sayfalarını kullanın.

## <a name="see-also"></a>Ayrıca bkz.

[Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)
