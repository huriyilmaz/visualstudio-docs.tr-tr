---
title: Uzaktan hata ayıklayıcı bağlantı noktası atamaları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 238bb4ec-bb00-4c2b-986e-18ac278f3959
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2628d8929a0d2b6fd3561f88c81cfaa3b62564f0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542109"
---
# <a name="remote-debugger-port-assignments"></a>Uzaktan Hata Ayıklayıcı Bağlantı Noktası Atamaları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio Uzaktan Hata Ayıklayıcı, bir uygulama veya arka plan hizmeti olarak çalıştırılabilir. Uygulama olarak çalıştırıldığında, varsayılan olarak aşağıdaki şekilde atanmış bir bağlantı noktası kullanır:  
  
- Visual Studio 2015:4020  
  
- Visual Studio 2013:4018  
  
- Visual Studio 2012:4016  
  
  Diğer bir deyişle, uzaktan hata ayıklayıcıya atanan bağlantı noktasının numarası, her sürüm için 2 ile artırılır. Dilediğiniz farklı bir bağlantı noktası numarası belirleyebilirsiniz. Daha sonraki bir bölümde bağlantı noktası numaralarının nasıl ayarlanacağını açıklayacağız.  
  
## <a name="the-remote-debugger-port-on-32-bit-operating-systems"></a>32 bit Işletim sistemlerinde uzaktan hata ayıklayıcı bağlantı noktası  
 TCP 4020 (Visual Studio 2015 ' de) ana bağlantı noktasıdır ve tüm senaryolar için gereklidir. Bunu komut satırından ya da uzaktan hata ayıklayıcı penceresinden yapılandırabilirsiniz.  
  
 Uzaktan hata ayıklayıcı penceresinde, **Araçlar/Seçenekler**' e tıklayın ve TCP/IP bağlantı noktası numarasını ayarlayın.  
  
 Komut satırında, **/Port** anahtarı: **msvsmon/Port \<port number> **ile uzaktan hata ayıklayıcıyı başlatın.  
  
 Uzaktan hata ayıklama yardımında tüm uzaktan hata ayıklayıcı komut satırı anahtarlarını bulabilir (uzaktan hata ayıklayıcı penceresinde **F1** tuşuna basın veya **Yardım/kullanım** ' ye tıklayabilirsiniz).  
  
## <a name="the-remote-debugger-port-on-64-bit-operating-systems"></a>64 bit Işletim sistemlerinde uzaktan hata ayıklayıcı bağlantı noktası  
 Uzaktan hata ayıklayıcının 64 bit sürümü başlatıldığında varsayılan olarak 4020 bağlantı noktasını kullanır.  32 bitlik bir işlemde hata ayıklaması yaparsanız, uzaktan hata ayıklayıcı 'nın 64 bit sürümü, bağlantı noktası 4021 üzerinde uzaktan hata ayıklayıcı 'nın 32 bit bir sürümünü başlatır. 32 bitlik uzaktan hata ayıklayıcıyı çalıştırırsanız, 4020 kullanır ve 4021 kullanılmaz.  
  
 Bu bağlantı noktası komut satırından yapılandırılabilir: **msvsmon/wow64port \<port number> **.  
  
## <a name="the-discovery-port"></a>Bulma bağlantı noktası  
 UDP 3702, ağda uzaktan hata ayıklayıcının çalışan örneklerini bulmak için kullanılır (örneğin, **Işleme İliştir** Iletişim kutusunda **bul** iletişim kutusu). Yalnızca uzaktan hata ayıklayıcıyı çalıştıran bir makineyi bulmak için kullanılır; bu nedenle, hedef bilgisayarın makine adını veya IP adresini bilmenin başka bir yolu varsa bu isteğe bağlıdır. Bu, bulma için standart bir bağlantı noktasıdır, bu nedenle bağlantı noktası numarası yapılandırılamaz.  
  
 Bulmayı etkinleştirmek istemiyorsanız, msvsmon 'yi bulma devre dışı:  **msvsmon/nodiscovery**ile komut satırından başlatabilirsiniz.  
  
## <a name="remote-debugger-ports-on-azure"></a>Azure 'da uzaktan hata ayıklayıcı bağlantı noktaları  
 Aşağıdaki bağlantı noktaları, Azure 'da uzaktan hata ayıklayıcı tarafından kullanılır. Bulut hizmetindeki bağlantı noktaları, tek bir VM 'deki bağlantı noktalarıyla eşleştirilir. Tüm bağlantı noktaları TCP ' dir.  

|**Bağlantı**|**Bulut hizmetindeki bağlantı noktası**|**VM 'deki bağlantı noktası**|  
|-|-|-|
|Microsoft. WindowsAzure. Eklentiler. RemoteDebugger. Connector|30400|30398|  
|Microsoft. WindowsAzure. Eklentiler. RemoteDebugger. Iletici|31400|31398|  
|Microsoft. WindowsAzure. Eklentiler. RemoteDebugger. FileUpload|32400|32398|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
