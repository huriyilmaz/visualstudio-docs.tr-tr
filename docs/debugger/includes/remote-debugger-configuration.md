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
ms.openlocfilehash: 2e5782c49f26925d9eda81f04653b1a20666c6b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89312112"
---
1. Uzak bilgisayarda, **Uzaktan hata ayıklayıcıyı** **Başlat** menüsünden bulun ve başlatın. 
   
   Uzak bilgisayarda yönetici izinleriniz yoksa, **Uzaktan hata ayıklayıcı** uygulamasına sağ tıklayın ve **yönetici olarak çalıştır**' ı seçin. Aksi takdirde, normal olarak başlatmanız yeterlidir.

   Yönetici olarak çalışan veya farklı bir kullanıcı hesabı altında (IIS gibi) çalışan bir işleme iliştirmeyi planlıyorsanız, **Uzaktan hata ayıklayıcı** uygulamasına sağ tıklayın ve **yönetici olarak çalıştır**' ı seçin. Daha fazla bilgi için bkz. [Uzaktan hata ayıklayıcıyı yönetici olarak çalıştırma](../remote-debugging-errors-and-troubleshooting.md#run-the-remote-debugger-as-an-administrator).
   
1. Uzaktan hata ayıklayıcıyı ilk kez başlattığınızda (veya yapılandırmadan önce), **Uzaktan hata ayıklama yapılandırması** iletişim kutusu görüntülenir.  
  
    ![Uzaktan hata ayıklayıcı yapılandırması](../media/remotedebuggerconfwizardpage.png "Uzaktan hata ayıklayıcı yapılandırması")  
  
1. Windows Web Hizmetleri API 'SI yüklü değilse ve yalnızca Windows Server 2008 R2 'de olduğunda, **yükleme** düğmesini seçin.  
  
1. Üzerinde Uzak araçları kullanmak istediğiniz en az bir ağ türü seçin. Bilgisayarlar bir etki alanı üzerinden bağlandıysa, ilk öğeyi seçmeniz gerekir. Bilgisayarlar bir çalışma grubu veya ev grubu üzerinden bağlandıysa, ikinci veya üçüncü öğeyi uygun şekilde seçin.  
  
1. Güvenlik duvarını yapılandırmak ve uzaktan hata ayıklayıcıyı başlatmak için **Uzaktan hata ayıklamayı Yapılandır** ' ı seçin.  
  
1. Yapılandırma tamamlandığında, **Uzaktan hata ayıklayıcı** penceresi görüntülenir.
  
    ![Uzaktan hata ayıklayıcı penceresi](../media/remotedebuggerwindow.png "Uzaktan hata ayıklayıcı penceresi")
  
    Uzaktan hata ayıklayıcı artık bir bağlantı bekliyor. Visual Studio 'da uzak bağlantı yapılandırmasını ayarlamak için gösterilen sunucu adını ve bağlantı noktası numarasını kullanın.  
  
Uzaktan hata ayıklayıcıyı durdurmak için **Dosya**  >  **Çıkış**' ı seçin. **Başlat** menüsünden veya komut satırından yeniden başlatabilirsiniz:  
  
```cmd
<Remote debugger installation directory>\msvsmon.exe
```
