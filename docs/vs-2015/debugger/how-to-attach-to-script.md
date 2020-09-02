---
title: 'Nasıl yapılır: betiğe Iliştirme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- script debugging, attaching to script
- script, attaching to
- processes, attaching to script
- remote debugging, attaching to script
ms.assetid: 82013e9a-ef53-4fd2-b451-a6891cdc6307
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 719654916087e7c7f4249ff52abbed628a2c56a2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704503"
---
# <a name="how-to-attach-to-script"></a>Nasıl Yapılır: Betiğe Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu, Visual Studio hata ayıklayıcısının hata ayıklama için bir komut dosyasına nasıl el ile iliştiriceğinizi açıklar.  
  
### <a name="to-attach-to-a-running-process"></a>Çalışan bir işleme iliştirmek için  
  
1. **Hata Ayıkla** menüsünde, **İşleme İliştir**' i seçin. (Proje açık değilse, **Araçlar** menüsünde **İşleme İliştir** ' i seçin.)  
  
2. **Işleme İliştir** iletişim kutusunda, **kullanılabilir işlemler** listesine bakın ve eklemek istediğiniz komut dosyası işlemini bulun. Komut dosyası süreçlerini **tür** sütununa bakarak tanımlayabilirsiniz.  
  
   1. Hata ayıklamak istediğiniz işlem başka bir bilgisayarda çalışıyorsa, önce uzak bilgisayarı seçmeniz gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: uzak bilgisayar seçme](https://msdn.microsoft.com/4332ba8e-2f0b-4f62-b96a-e762b9f3c3ba).  
  
   2. İşlem farklı bir kullanıcı hesabı altında çalışıyorsa, **tüm kullanıcılardan Işlemleri göster** onay kutusunu seçin.  
  
   3. **Uzak Masaüstü bağlantısı**aracılığıyla bağlandıysanız, **tüm oturumlarda işlem göster** onay kutusunu seçin.  
  
3. Eklemek istediğiniz işleme tıklayın.  
  
4. **İliştirme** kutusunda, **betik kodu** veya **Otomatik: betik kodu**görmeniz gerekir. Başka bir şey görürseniz, aşağıdaki adımları izleyin:  
  
   1. **Seç**’e tıklayın.  
  
   2. **Kod türünü seç** iletişim kutusunda, **Bu kod türlerinde hata ayıkla** ' ya tıklayın ve **komut dosyası**' nı seçin.  
  
   3. **Tamam**’a tıklayın.  
  
5. **Ekle**' ye tıklayın.  
  
    Bu noktada, Internet Explorer 'da betik hata ayıklamanın devre dışı bırakıldığını bildiren bir uyarı görebilirsiniz. Böyle bir durumla karşılaşırsanız bkz. [Uyarı: betik hata ayıklaması devre dışı](../debugger/warning-script-debugging-disabled.md).  
  
   **İşler** iletişim kutusunu açtığınızda **kullanılabilir süreçler** listesi otomatik olarak görüntülenir. İletişim kutusu açıkken, işlem arka planda başlayabilir ve durabilir. Bu nedenle, içerikler her zaman güncel olmayabilir. **Yenile** düğmesine basarak, geçerli işlem listesini görmek için istediğiniz zaman listeyi yenileyebilirsiniz.  
  
   Hata ayıklarken birden çok programa iliştirilebilir, ancak herhangi bir zamanda hata ayıklayıcıda yalnızca bir program etkin hale getirebilirsiniz. Hata ayıklama konumu araç çubuğunda etkin programı ayarlayabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: geçerli Işlemi ayarlama](https://msdn.microsoft.com/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).  
  
   Tüm **hata ayıklama** menüsü yürütme komutları etkin programı etkiler. Herhangi bir hata ayıklama programını süreçler iletişim kutusundan kesebilirsiniz. Bkz. [kesme noktaları kullanma](../debugger/using-breakpoints.md).  
  
> [!NOTE]
> Güvenilmeyen bir kullanıcı hesabına ait olan bir işleme iliştirmeye çalışırsanız, bir güvenlik uyarısı iletişim kutusu onayı görüntülenir. Daha fazla bilgi için bkz [. güvenlik uyarısı: güvenilmeyen bir kullanıcının sahip olduğu bir Işleme ekleme tehlikeli olabilir. Aşağıdaki bilgiler şüpheli görünüyorsa veya emin değilseniz, bu işleme](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015)eklemeyin.  
  
 Bazı durumlarda, bir Terminal Hizmetleri (Uzak Masaüstü) oturumunda hata ayıklarken, kullanılabilir süreçler listesinde tüm kullanılabilir süreçler görüntülenmez. [!INCLUDE[WinXPSvr](../includes/winxpsvr-md.md)]Veya sonraki sürümlerde, Visual Studio 'yu sınırlı bir kullanıcı olarak çalıştırıyorsanız, kullanılabilir süreçler listesi w3wp.exe dahil olmak üzere Hizmetler ve diğer sunucu işlemlerinde kullanılan oturum 0 ' da çalışan işlemi göstermez. Visual Studio 'Yu bir yönetici hesabı altında veya bir Terminal Hizmetleri oturumu yerine sunucu konsolundan çalıştırarak sorunu çözebilirsiniz. Bu geçici çözümlerin hiçbiri mümkün değilse, Windows komut satırında vsjitdebugger.exe-p Işlem kimliği yazarak işleme eklemek üçüncü bir seçenektir. tlist.exe kullanarak işlem kimliğini belirleyebilirsiniz. tlist.exe edinmek için Windows [donanım Geliştirici Merkezi](https://developer.microsoft.com/windows/hardware)' nde bulunan Windows Için hata ayıklama araçları 'nı indirip yükleyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İstemci tarafı betik hata ayıklaması](../debugger/client-side-script-debugging.md)   
 [Çalışan Işlemlere iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Güvenlik Uyarısı: güvenilmeyen bir kullanıcının sahip olduğu bir işleme ekleme tehlikeli olabilir. Aşağıdaki bilgiler şüpheli görünüyorsa veya emin değilseniz, bu işleme eklemeyin](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015)   
 [Hata Ayıklama Güvenliği](../debugger/debugger-security.md)
