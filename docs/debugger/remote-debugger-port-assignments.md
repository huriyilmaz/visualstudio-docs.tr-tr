---
title: Uzaktan Hata Ayıklayıcı Bağlantı Noktası Atamaları | Microsoft Docs
description: 32 bit Visual Studio, 64 bit işletim sistemleri ve Azure'da uzaktan hata ayıklayıcı bağlantı noktası atamalarını anlıyoruz. Bulma bağlantı noktası hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 09/10/2021
ms.topic: reference
ms.assetid: 238bb4ec-bb00-4c2b-986e-18ac278f3959
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9eacb91faa204f92b63ecf464c1ef418b387e38a
ms.sourcegitcommit: 64d6c5cf93984bbb22812577af17128cd2239f79
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2021
ms.locfileid: "134366949"
---
# <a name="remote-debugger-port-assignments"></a>Uzaktan Hata Ayıklayıcı Bağlantı Noktası Atamaları
Bu Visual Studio Uzaktan Hata Ayıklayıcı uygulama olarak veya arka plan hizmeti olarak çalışır. Uygulama olarak çalıştırdığı zaman, varsayılan olarak atanan bir bağlantı noktasını aşağıdaki gibi kullanır:

- Visual Studio 2022: 4026

- Visual Studio 2019: 4024

- Visual Studio 2017: 4022

- Visual Studio 2015: 4020

- Visual Studio 2013: 4018

- Visual Studio 2012: 4016

Başka bir deyişle, uzak hata ayıklayıcıya atanan bağlantı noktası sayısı her sürüm için 2 artırılır. Like you can set a different port number. Sonraki bir bölümde bağlantı noktası numaralarını ayarlamayı açıklayacağız.

## <a name="the-remote-debugger-port-on-32-bit-operating-systems"></a>32 bit İşletim Sistemlerinde Uzaktan Hata Ayıklayıcı Bağlantı Noktası

::: moniker range=">=vs-2022"
 TCP 4026 (Visual Studio 2022'de) ana bağlantı noktasıdır ve tüm senaryolar için gereklidir. Bunu komut satırı veya uzaktan hata ayıklayıcısı penceresinden yapılandırabilirsiniz.
::: moniker-end
::: moniker range="vs-2019"
 TCP 4024 (Visual Studio 2019'da) ana bağlantı noktasıdır ve tüm senaryolar için gereklidir. Bunu komut satırı veya uzaktan hata ayıklayıcısı penceresinden yapılandırabilirsiniz.
::: moniker-end
::: moniker range="vs-2017"
 TCP 4022 (Visual Studio 2017'de) ana bağlantı noktasıdır ve tüm senaryolar için gereklidir. Bunu komut satırı veya uzaktan hata ayıklayıcısı penceresinden yapılandırabilirsiniz.
::: moniker-end

 Uzaktan hata ayıklayıcısı penceresinde Araçlar ve **Seçenekler'>'ye** tıklayın ve TCP/IP bağlantı noktası numarasını ayarlayın.

 Komut satırına **/port** switch: msvsmon /port komutuyla **uzak hata ayıklayıcısını başlatabilirsiniz. \<port number>**

 Tüm uzaktan hata ayıklayıcı komut satırı anahtarlarını uzaktan hata ayıklama yardımında bulabilirsiniz **(F1** tuşuna basın veya uzaktan hata ayıklayıcı **penceresinde** >'a tıklayın).

## <a name="the-remote-debugger-port-on-64-bit-operating-systems"></a>64 bit İşletim Sistemlerinde Uzaktan Hata Ayıklayıcı Bağlantı Noktası
::: moniker range=">=vs-2022"
 Uzak hata ayıklayıcının 64 bit sürümü başlatıcı, varsayılan olarak ana bağlantı noktasını (4026) kullanır.  32 bit işlemde hata ayıklarsanız, uzak hata ayıklayıcının 64 bit sürümü, 4025 bağlantı noktası üzerinde uzaktan hata ayıklayıcının 32 bit sürümünü başlatır. 32 bit uzaktan hata ayıklayıcısını kullanırsanız, 4026 kullanır ve 4025 kullanılmaz.
::: moniker-end
::: moniker range="vs-2019"
 Uzak hata ayıklayıcının 64 bit sürümü başlatıcı, varsayılan olarak ana bağlantı noktasını (4024) kullanır.  32 bit işlemde hata ayıklarsanız, uzak hata ayıklayıcının 64 bit sürümü, 4025 numaralı bağlantı noktası üzerinde uzak hata ayıklayıcının 32 bit sürümünü başlatır (ana bağlantı noktası numarası 1 artırılır). 32 bit uzaktan hata ayıklayıcısını kullanırsanız, 4024 kullanır ve 4025 kullanılmaz.
::: moniker-end
::: moniker range="vs-2017"
 Uzak hata ayıklayıcının 64 bit sürümü başlatıcı, varsayılan olarak ana bağlantı noktasını (4022) kullanır.  32 bit işlemde hata ayıklarsanız, uzak hata ayıklayıcının 64 bit sürümü, 4023 numaralı bağlantı noktası üzerinde uzak hata ayıklayıcının 32 bit sürümünü başlatır (ana bağlantı noktası numarası 1 artırılır). 32 bit uzaktan hata ayıklayıcısını kullanırsanız, 4022 kullanır ve 4023 kullanılmaz.
:::moniker-end

 Bu bağlantı noktası komut satırıyla yapılandırılabilir: **Msvsmon \<port number> /wow64port**.

## <a name="the-discovery-port"></a>Bulma Bağlantı Noktası
 UDP 3702, ağ üzerinde uzak hata ayıklayıcının çalışan örneklerini bulmak  için kullanılır (örneğin İşleme Ekle iletişim kutusundaki Bul **iletişim** kutusu). Yalnızca uzak hata ayıklayıcısını çalıştıran bir makineyi bulmak için kullanılır, bu nedenle hedef bilgisayarın makine adını veya IP adresini öğrenmenin başka bir yolu varsa isteğe bağlıdır. Bu, bulma için standart bir bağlantı noktasıdır, bu nedenle bağlantı noktası numarası yapılandıramaz.

 Bulmayı etkinleştirmek istemiyorsanız, msvsmon'ı komut satırına bulma devre dışı bırakarak  **başlatabilirsiniz: Msvsmon /nodiscovery**.

## <a name="remote-debugger-ports-on-azure"></a>Azure'da Uzaktan Hata Ayıklayıcı Bağlantı Noktaları
 Aşağıdaki bağlantı noktaları Azure'da uzaktan hata ayıklayıcı tarafından kullanılır. Bulut hizmeti bağlantı noktaları, tek tek VM'ler üzerinde yer alan bağlantı noktalarıyla eşlenmiş. Tüm bağlantı noktaları TCP'dir.

|Bağlantı|Bulut Hizmeti'ne bağlantı noktası|VM'de bağlantı noktası|
|-|-|-|
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector|30400|30398|
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Forwarder|31400|31398|
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Forwarderx86|31401|31399|
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.FileUpload|32400|32398|

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md)
