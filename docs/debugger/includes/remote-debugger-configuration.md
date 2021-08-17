---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 3994f1bbbf707fad59907d0bd178f61a9629c32f498bb179f8edaa24ff1d2cf5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "122058335"
---
1. Uzak bilgisayarda, Başlat menüsünden Uzaktan **Hata Ayıklayıcı'sını** bulun **ve** başlatın. 
   
   Uzak bilgisayarda yönetici izinlerine sahip değilseniz, Uzaktan Hata Ayıklayıcı uygulamasına sağ tıklayın ve **Yönetici** olarak **çalıştır'ı seçin.** Aksi takdirde normal şekilde başlat.

   Yönetici olarak çalışan veya farklı bir kullanıcı hesabı (IIS gibi) altında çalışan bir işleme ekleme yapmayı  planlıyorsanız, Uzaktan Hata Ayıklayıcı uygulamasına sağ tıklayın ve Yönetici olarak **çalıştır'ı seçin.** Daha fazla bilgi için [bkz. Uzak hata ayıklayıcıyı yönetici olarak çalıştırma.](../remote-debugging-errors-and-troubleshooting.md#run-the-remote-debugger-as-an-administrator)
   
1. Uzaktan hata ayıklayıcıyı ilk kez başlatmanız (veya yapılandırmadan önce), Uzaktan Hata Ayıklama **Yapılandırması iletişim** kutusu görüntülenir.  
  
    ![Uzaktan Hata Ayıklayıcı yapılandırması](../media/remotedebuggerconfwizardpage.png "Uzaktan Hata Ayıklayıcı yapılandırması")  
  
1. Windows Server 2008 R2'de yalnızca Windows Web Hizmetleri API'si yüklüyse Yükle **düğmesini** seçin.  
  
1. Uzak araçları kullanmak istediğiniz en az bir ağ türünü seçin. Bilgisayarlar bir etki alanı üzerinden bağlı ise, ilk öğeyi seçmeniz gerekir. Bilgisayarlar bir çalışma grubu veya ev grubu üzerinden bağlıysa, uygun şekilde ikinci veya üçüncü öğeyi seçin.  
  
1. Güvenlik **duvarını yapılandırmak ve uzaktan** hata ayıklayıcıyı başlatmak için Uzaktan hata ayıklamayı yapılandır'ı seçin.  
  
1. Yapılandırma tamamlandığında, Uzaktan **Hata Ayıklayıcı penceresi** görüntülenir.
  
    ![Uzaktan Hata Ayıklayıcısı penceresi](../media/remotedebuggerwindow.png "Uzaktan Hata Ayıklayıcısı penceresi")
  
    Uzak hata ayıklayıcı artık bağlantı bekliyor. Sunucu adı ve bağlantı noktası numarasını kullanarak uzak bağlantı yapılandırmasını Visual Studio.  
  
Uzaktan hata ayıklayıcıyı durdurmak için Dosya **Çıkış'ı**  >  **seçin.** Başlat menüsünden veya **komut** satırına bakarak yeniden başlatabilirsiniz:  
  
```cmd
<Remote debugger installation directory>\msvsmon.exe
```
