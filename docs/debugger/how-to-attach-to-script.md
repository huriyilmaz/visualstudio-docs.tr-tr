---
title: 'Nasıl yapılır: betiğe Iliştirme | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- script debugging, attaching to script
- script, attaching to
- processes, attaching to script
- remote debugging, attaching to script
ms.assetid: 82013e9a-ef53-4fd2-b451-a6891cdc6307
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9e4668cc991c4b46fb69d7ec6973ab4d8630e14b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72733953"
---
# <a name="how-to-attach-to-script"></a>Nasıl Yapılır: Betiğe Ekleme
Bu konu, Visual Studio hata ayıklayıcısının hata ayıklama için bir komut dosyasına nasıl el ile iliştiriceğinizi açıklar.

### <a name="to-attach-to-a-running-process"></a>Çalışan bir işleme iliştirmek için

1. **Hata Ayıkla** menüsünde, **İşleme İliştir**' i seçin. (Proje açık değilse, **Araçlar** menüsünde **İşleme İliştir** ' i seçin.)

2. **Işleme İliştir** iletişim kutusunda, **kullanılabilir işlemler** listesine bakın ve eklemek istediğiniz komut dosyası işlemini bulun. Komut dosyası süreçlerini **tür** sütununa bakarak tanımlayabilirsiniz.

   1. Hata ayıklamak istediğiniz işlem başka bir bilgisayarda çalışıyorsa, önce uzak bilgisayarı seçmeniz gerekir.

   2. İşlem farklı bir kullanıcı hesabı altında çalışıyorsa, **tüm kullanıcılardan Işlemleri göster** onay kutusunu seçin.

   3. **Uzak Masaüstü bağlantısı**aracılığıyla bağlandıysanız, **tüm oturumlarda işlem göster** onay kutusunu seçin.

3. Eklemek istediğiniz işleme tıklayın.

4. **İliştirme** kutusunda, **betik kodu** veya **Otomatik: betik kodu**görmeniz gerekir. Başka bir şey görürseniz, aşağıdaki adımları izleyin:

   1. **Seç**' e tıklayın.

   2. **Kod türünü seç** iletişim kutusunda, **Bu kod türlerinde hata ayıkla** ' ya tıklayın ve **komut dosyası**' nı seçin.

   3. **Tamam**'a tıklayın.

5. **Ekle**' ye tıklayın.

    Bu noktada, Internet Explorer 'da betik hata ayıklamanın devre dışı bırakıldığını bildiren bir uyarı görebilirsiniz. Böyle bir durumla karşılaşırsanız bkz. [Uyarı: betik hata ayıklaması devre dışı](../debugger/warning-script-debugging-disabled.md).

   **İşler** iletişim kutusunu açtığınızda **kullanılabilir süreçler** listesi otomatik olarak görüntülenir. İletişim kutusu açıkken, işlem arka planda başlayabilir ve durabilir. Bu nedenle, içerikler her zaman güncel olmayabilir. **Yenile** düğmesine basarak, geçerli işlem listesini görmek için istediğiniz zaman listeyi yenileyebilirsiniz.

   Hata ayıklarken birden çok programa iliştirilebilir, ancak herhangi bir zamanda hata ayıklayıcıda yalnızca bir program etkin hale getirebilirsiniz. Hata ayıklama konumu araç çubuğunda etkin programı ayarlayabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: geçerli Işlemi ayarlama](/previous-versions/visualstudio/visual-studio-2010/d5d4sxdw(v=vs.100)).

   Tüm **hata ayıklama** menüsü yürütme komutları etkin programı etkiler. Herhangi bir hata ayıklama programını süreçler iletişim kutusundan kesebilirsiniz. Bkz. [kesme noktaları kullanma](../debugger/using-breakpoints.md).

> [!NOTE]
> Güvenilmeyen bir kullanıcı hesabına ait olan bir işleme iliştirmeye çalışırsanız, bir güvenlik uyarısı iletişim kutusu onayı görüntülenir. Daha fazla bilgi için bkz [. güvenlik uyarısı: güvenilmeyen bir kullanıcının sahip olduğu bir Işleme ekleme tehlikeli olabilir. Aşağıdaki bilgiler şüpheli görünüyorsa veya emin değilseniz, bu işleme](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)eklemeyin.

 Bazı durumlarda, bir Terminal Hizmetleri (Uzak Masaüstü) oturumunda hata ayıklarken, kullanılabilir süreçler listesinde tüm kullanılabilir süreçler görüntülenmez. @No__t_0 veya sonraki sürümlerde, Visual Studio 'Yu sınırlı bir kullanıcı olarak çalıştırıyorsanız, kullanılabilir süreçler listesi, W3wp. exe dahil olmak üzere Hizmetler ve diğer sunucu işlemlerinde kullanılan oturum 0 ' da çalışan işlemlerin gösterilmeyecektir. Visual Studio 'Yu bir yönetici hesabı altında veya bir Terminal Hizmetleri oturumu yerine sunucu konsolundan çalıştırarak sorunu çözebilirsiniz. Bu geçici çözümlerin hiçbiri mümkün değilse, Windows komut satırında vsjıtdebugger. exe-p Işlem kimliği yazarak işleme eklemek üçüncü bir seçenektir. İşlem kimliğini Tlist. exe ' yi kullanarak belirleyebilirsiniz. Tlist. exe ' yi edinmek için Windows [donanım Geliştirici Merkezi](/windows-hardware/drivers/dashboard/)' nde bulunan Windows Için hata ayıklama araçları 'nı indirip yükleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [İstemci Tarafı Betikte Hata Ayıklama](../debugger/client-side-script-debugging.md)
- [Çalıştırma İşlemine İliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Güvenlik Uyarısı: güvenilmeyen bir kullanıcının sahip olduğu bir işleme ekleme tehlikeli olabilir. Aşağıdaki bilgiler şüpheli görünüyorsa veya emin değilseniz, bu işleme eklemeyin](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
- [Hata Ayıklayıcısı Güvenliği](../debugger/debugger-security.md)