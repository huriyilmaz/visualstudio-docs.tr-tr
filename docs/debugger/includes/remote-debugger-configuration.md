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
ms.openlocfilehash: 60903da92c98305162518b783de207b369401cf3
ms.sourcegitcommit: 7a300823cf1bd3355be03bde561cf2777bc09eae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2021
ms.locfileid: "134163969"
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
  
    ::: moniker range=">= vs-2022"
    ![Uzaktan Hata Ayıklayıcısı penceresi](../media/vs-2022/remote-debugger-window.png "Uzaktan Hata Ayıklayıcısı penceresi")
    ::: moniker-end
    ::: moniker range="<= vs-2019"
    ![Uzaktan Hata Ayıklayıcısı penceresi](../media/remotedebuggerwindow.png "Uzaktan Hata Ayıklayıcısı penceresi")
    ::: moniker-end
  
    Uzak hata ayıklayıcı artık bağlantı bekliyor. Sunucu adı ve bağlantı noktası numarasını kullanarak sunucu içinde uzak bağlantı yapılandırmasını Visual Studio.  
  
Uzaktan hata ayıklayıcıyı durdurmak için Dosya **Çıkış'ı**  >  **seçin.** Başlat menüsünden veya **komut** satırına bakarak yeniden başlatabilirsiniz:  
  
```cmd
<Remote debugger installation directory>\msvsmon.exe
```
