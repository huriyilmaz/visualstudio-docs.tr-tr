---
title: 'Nasıl yapılır: komut satırından sembol dosyası konumlarını belirtme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 8aa067bb-e8bf-4081-aff0-cfbcf65934a0
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5ed6ddc11a998d97a193c2ab01ff69d386ed4ffe
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77476974"
---
# <a name="how-to-specify-symbol-file-locations-from-the-command-line"></a>Nasıl yapılır: Simge Dosyası Konumlarını Komut Satırından Belirtme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İşlev adları ve satır numaraları gibi simge bilgilerini göstermek için, VSPerfReport komut satırı aracı, profili oluşturulmuş bileşenlerin ve Windows sistem dosyalarının sembol (. pdb) dosyalarına erişim gerektirir. Sembol dosyaları bir bileşen derlendiğinde oluşturulur. Daha fazla bilgi için bkz. [VSPerfReport](../profiling/vsperfreport.md). VSPerfReport sembol dosyaları için aşağıdaki konumları otomatik olarak arar:  
  
- **/SymbolPath** seçeneğinde veya **_NT_SYMBOL_PATH** ortam değişkeninde belirtilen yollar.  
  
- Bir bileşenin derlendiği tam yerel yol.  
  
- Profil oluşturma verileri (. vsp veya. vsps) dosyasını içeren dizin.  
  
  Microsoft, bir sembol sunucusunda birçok ürününün çevrimiçi olarak. pdb dosyalarını sağlar. Raporlama için kullandığınız bilgisayar Internet 'e bağlıysa, VSPerfReport sembol bilgilerini otomatik olarak aramak ve dosyaları yerel bir depoya kaydetmek için çevrimiçi sembol sunucusuna bağlanır.  
  
  Sembol dosyalarının ve Microsoft sembol sunucusu deposunun konumunu aşağıdaki yollarla belirtebilirsiniz:  
  
- **_NT_SYMBOL_PATH** ortam değişkenini ayarlayın.  
  
- VSPerfReport komut satırına **/SymbolPath** seçeneğini ekleyin.  
  
  Bu yöntemlerin her ikisini de kullanabilirsiniz.  
  
> [!NOTE]
> Yerel bilgisayarda [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yüklüyse, büyük olasılıkla Windows sembol dosyaları için bir konum belirtilmiş olmalıdır. Daha fazla bilgi için bkz. [nasıl yapılır: başvuru Windows sembol bilgileri](../profiling/how-to-reference-windows-symbol-information.md). Yine de bu konunun ilerleyen kısımlarında açıklandığı gibi, konum ve sunucuyu kullanmak için VSPerfReport 'ı yapılandırmanız gerekir.  
  
## <a name="specifying-windows-symbol-files"></a>Windows sembol dosyalarını belirtme  
  
#### <a name="to-configure-the-use-of-the-windows-symbol-server"></a>Windows sembol sunucusu kullanımını yapılandırmak için  
  
1. Gerekirse, sembol dosyalarını yerel olarak depolamak için bir dizin oluşturun.  
  
2. **_NT_SYMBOL_PATH** ortam değişkenini veya VSPerfReport/SymbolPath seçeneğini ayarlamak için aşağıdaki sözdizimini kullanın:  
  
    `srv*<LocalStore>*https://msdl.microsoft.com/downloads/symbols`  
  
    Burada *<LocalStore>* , oluşturduğunuz yerel dizinin yoludur.  
  
## <a name="specifying-component-symbol-files"></a>Bileşen sembol dosyalarını belirtme  
 Profil Oluşturma Araçları, içinde veya profil oluşturma veri dosyasını içeren klasörde depolanan özgün konumlarında profil oluşturmak istediğiniz bileşenlerin. pdb dosyalarını arar. **_NT_SYMBOL_PATH** veya **/SymbolPath** seçeneğine bir veya daha fazla yol ekleyerek arama yapmak için başka konumlar belirleyebilirsiniz. Yolları noktalı virgülle ayırın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut satırı, **_NT_SYMBOL_PATH** ortam değişkenini Windows sembol sunucusuna ve yerel dizini **c:\symbols**olarak ayarlar.  
  
 ```cmd
 set  _NT_SYMBOL_PATH=srv*C:\symbols*https://msdl.microsoft.com/downloads/symbols`  
 ```
  
 Aşağıdaki VSPerfReport komut satırı, **/SymbolPath** seçeneğini kullanarak C:\projelersymbols dizinini arama yoluna ekler.  
  
 **VSPerfReport**  *MyApp* **. exe/SymbolPath: c:\projelerteksymbols/Summary: ALL**
