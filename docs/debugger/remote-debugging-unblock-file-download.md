---
title: Uzak araçların indirme engelini kaldırma
description: Varsayılan IE güvenlik ayarları nedeniyle zaman alıcı Windows Sunucu'da uzak araçların indirme engelini kaldırabilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 07/19/2018
ms.topic: troubleshooting
helpviewer_keywords:
- remote debugging, unblock download
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 8ec0b81a6e97faf6a3dae42ea90a66cb62fb57c7
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627896"
---
# <a name="how-to-unblock-the-download-of-the-remote-tools-on-windows-server"></a>Nasıl kullanılır: Windows Server'da uzak araçların indir Windows kaldırma

Windows Server'Internet Explorer'daki varsayılan güvenlik ayarları, uzak araçlar gibi bileşenleri indirmeyi zaman alabilir.

* Gelişmiş Güvenlik Yapılandırması Internet Explorer etkinleştirildiğinden, kaynağı içeren etki alanına açıkça izin verilmediği (yani güvenilen) sürece web sitelerini açmanız ve web kaynaklarına erişmeniz önlenebilir. Bu ayarı devre dışı bırakabilirsiniz ancak güvenlik riski suna olduğundan bunu önerilmez.

* Bu Windows Server 2016 İnternet Seçenekleri Güvenliği İnternet Özel Düzeyi **İndirmeleri'nin**  >  **varsayılan**  >    >  **ayarı**  >   dosya indirmelerini de devre dışı bırakır. Uzak araçları doğrudan Windows Server'a indirmeyi seçerseniz, dosya indirmeyi etkinleştirmeniz gerekir.

Araçları Windows Server'a indirmek için aşağıdaki eylemlerden birini öneririz:

* Uzak araçları çalıştıran bilgisayar gibi farklı bir bilgisayara indirin Visual Studio ve.exe *Windows* Server'a kopyalayın.

* Uzak hata ayıklayıcıyı [makinenizin dosya paylaşımından](../debugger/remote-debugging.md#fileshare_msvsmon) Visual Studio çalıştırın.

* Uzak araçları doğrudan Windows Server'a indirin ve güvenilen siteler ekleme istemlerini kabul edin. Modern web siteleri genellikle birçok üçüncü taraf kaynağı içerir ve bu da birçok istemle sonuçlandırabilir. Ayrıca, yeniden yönlendirilen tüm bağlantıların el ile ekleniyor olması gerekebilir. İndirmeye başlamadan önce güvenilen sitelerden bazılarını indirebilirsiniz. İnternet **Siteleri'ne > Güvenlik > Siteleri'ne > ve** aşağıdaki siteleri ekleyin.

  * visualstudio.microsoft.com
  * download.visualstudio.microsoft.com
  * about:blank

  My.visualstudio.com'da hata ayıklayıcısının eski sürümleri için, oturum açmanın başarılı olduğundan emin olmak için şu diğer siteleri ekleyin:

  * microsoft.com
  * go.microsoft.com
  * download.microsoft.com
  * my.visualstudio.com
  * login.microsoftonline.com
  * login.live.com
  * secure.aadcdn.microsoftonline-p.com
  * msft.sts.microsoft.com
  * auth.gfx.ms
  * app.vssps.visualstudio.com
  * vlscppe.microsoft.com
  * query.prod.cms.rt.microsoft.com

    Uzak araçları indirirken bu etki alanlarını eklemeyi seçerseniz, istendiğinde **Ekle'yi** seçin.

    ![Engellenen içerik iletişim kutusu](../debugger/media/remotedbg-blocked-content.png)

    Yazılımı indirip çeşitli web sitesi betiklerini ve kaynaklarını yükleme izni vermek için daha fazla istek alacaktır. Bu my.visualstudio.com oturum açmanın başarılı olduğundan emin olmak için ek etki alanlarını eklemenizi öneririz.