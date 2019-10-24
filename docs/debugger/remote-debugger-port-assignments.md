---
title: Uzaktan hata ayıklayıcı bağlantı noktası atamaları | Microsoft Docs
ms.custom: ''
ms.date: 05/18/2018
ms.topic: reference
ms.assetid: 238bb4ec-bb00-4c2b-986e-18ac278f3959
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf3d3ce704d517224452731c52a891ac2263f738
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72730249"
---
# <a name="remote-debugger-port-assignments"></a>Uzaktan Hata Ayıklayıcı Bağlantı Noktası Atamaları
Visual Studio Uzaktan Hata Ayıklayıcı, bir uygulama veya arka plan hizmeti olarak çalıştırılabilir. Uygulama olarak çalıştırıldığında, varsayılan olarak aşağıdaki şekilde atanmış bir bağlantı noktası kullanır:
::: moniker range=">=vs-2019"
- Visual Studio 2019:4024
::: moniker-end
- Visual Studio 2017:4022

- Visual Studio 2015:4020

- Visual Studio 2013:4018

- Visual Studio 2012:4016

  Diğer bir deyişle, uzaktan hata ayıklayıcıya atanan bağlantı noktasının numarası, her sürüm için 2 ile artırılır. Dilediğiniz farklı bir bağlantı noktası numarası belirleyebilirsiniz. Daha sonraki bir bölümde bağlantı noktası numaralarının nasıl ayarlanacağını açıklayacağız.

## <a name="the-remote-debugger-port-on-32-bit-operating-systems"></a>32 bit Işletim sistemlerinde uzaktan hata ayıklayıcı bağlantı noktası

::: moniker range=">=vs-2019"
 TCP 4024 (Visual Studio 2019 ' de) ana bağlantı noktasıdır ve tüm senaryolar için gereklidir. Bunu komut satırından ya da uzaktan hata ayıklayıcı penceresinden yapılandırabilirsiniz.
::: moniker-end
::: moniker range="vs-2017"
 TCP 4022 (Visual Studio 2017 ' de) ana bağlantı noktasıdır ve tüm senaryolar için gereklidir. Bunu komut satırından ya da uzaktan hata ayıklayıcı penceresinden yapılandırabilirsiniz.
::: moniker-end

 Uzaktan hata ayıklayıcı penceresinde **araçlar > seçenekler**' e tıklayın ve TCP/IP bağlantı noktası numarasını ayarlayın.

 Komut satırında, uzaktan hata ayıklayıcıyı **/Port** anahtarıyla başlatın: **msvsmon/port \<port Number >** .

 Uzaktan hata ayıklama yardımında tüm uzaktan hata ayıklayıcı komut satırı anahtarlarını bulabilir (uzaktan hata ayıklayıcı penceresinde **F1** ' e basın veya **Yardım > yardım** ' a tıklayabilirsiniz).

## <a name="the-remote-debugger-port-on-64-bit-operating-systems"></a>64 bit Işletim sistemlerinde uzaktan hata ayıklayıcı bağlantı noktası
::: moniker range=">=vs-2019"
 Uzaktan hata ayıklayıcının 64 bit sürümü başlatıldığında, varsayılan olarak ana bağlantı noktasını (4024) kullanır.  32 bitlik bir işlemde hata ayıklaması yaparsanız, uzaktan hata ayıklayıcı 'nın 64 bit sürümü, bağlantı noktası 4025 (1 ile artırılan ana bağlantı noktası numarası) üzerinde uzaktan hata ayıklayıcı 'nın 32 bit sürümünü başlatır. 32 bitlik uzaktan hata ayıklayıcıyı çalıştırırsanız, 4024 kullanır ve 4025 kullanılmaz.
::: moniker-end
::: moniker range="vs-2017"
 Uzaktan hata ayıklayıcının 64 bit sürümü başlatıldığında, varsayılan olarak ana bağlantı noktasını (4022) kullanır.  32 bitlik bir işlemde hata ayıklaması yaparsanız, uzaktan hata ayıklayıcı 'nın 64 bit sürümü, bağlantı noktası 4023 (1 ile artırılan ana bağlantı noktası numarası) üzerinde uzaktan hata ayıklayıcı 'nın 32 bit sürümünü başlatır. 32 bitlik uzaktan hata ayıklayıcıyı çalıştırırsanız, 4022 kullanır ve 4023 kullanılmaz.
:::moniker-end

 Bu bağlantı noktası komut satırından yapılandırılabilir: **msvsmon/wow64port \<port number >** .

## <a name="the-discovery-port"></a>Bulma bağlantı noktası
 UDP 3702, ağda uzaktan hata ayıklayıcının çalışan örneklerini bulmak için kullanılır (örneğin, **Işleme İliştir** Iletişim kutusunda **bul** iletişim kutusu). Yalnızca uzaktan hata ayıklayıcıyı çalıştıran bir makineyi bulmak için kullanılır; bu nedenle, hedef bilgisayarın makine adını veya IP adresini bilmenin başka bir yolu varsa bu isteğe bağlıdır. Bu, bulma için standart bir bağlantı noktasıdır, bu nedenle bağlantı noktası numarası yapılandırılamaz.

 Bulmayı etkinleştirmek istemiyorsanız, msvsmon 'yi bulma devre dışı: **msvsmon/nodiscovery**ile komut satırından başlatabilirsiniz.

## <a name="remote-debugger-ports-on-azure"></a>Azure 'da uzaktan hata ayıklayıcı bağlantı noktaları
 Aşağıdaki bağlantı noktaları, Azure 'da uzaktan hata ayıklayıcı tarafından kullanılır. Bulut hizmetindeki bağlantı noktaları, tek bir VM 'deki bağlantı noktalarıyla eşleştirilir. Tüm bağlantı noktaları TCP ' dir.

|Bağlanma|Bulut hizmetindeki bağlantı noktası|VM 'deki bağlantı noktası|
|-|-|-|
|Microsoft. WindowsAzure. Eklentiler. RemoteDebugger. Connector|30400|30398|
|Microsoft. WindowsAzure. Eklentiler. RemoteDebugger. Iletici|31400|31398|
|Microsoft. WindowsAzure. Eklentiler. RemoteDebugger. Forwarderx86|31401|31399|
|Microsoft. WindowsAzure. Eklentiler. RemoteDebugger. FileUpload|32400|32398|

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md)