---
title: Uzak Araçlar indirmenin engellemesini kaldır
description: Windows sunucuda uzak araçların indirilmesini engellemeyi kaldırın ve bu, varsayılan ıe güvenlik ayarları nedeniyle zaman alıcı olabilir.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122153803"
---
# <a name="how-to-unblock-the-download-of-the-remote-tools-on-windows-server"></a>nasıl yapılır: Windows sunucuda uzak araçların indirilmesini kaldırma

Windows Server 'daki ınternet Explorer 'daki varsayılan güvenlik ayarları, uzak araçlar gibi bileşenlerin indirileceği zaman alıcı olabilir.

* Gelişmiş güvenlik yapılandırması, Internet Explorer 'da etkinleştirilir ve bu da, kaynağı içeren etki alanına açıkça izin verilmediği (yani, güvenilen) Web sitelerini açmanızı ve Web kaynaklarına erişmenizi önler. Bu ayarı devre dışı bırakabilseniz de, bir güvenlik riski sunabileceğinden bunu önermiyoruz.

* Windows Server 2016, **ınternet seçenekleri**  >  **güvenliği**  >  **ınternet**  >  **özel düzeyi**  >  **indirmelerinde** varsayılan bir ayar de dosya indirmelerini devre dışı bırakır. uzak araçları doğrudan Windows sunucusuna indirmeyi seçerseniz, dosya indirmeyi etkinleştirmeniz gerekir.

araçları Windows sunucusuna indirmek için aşağıdaki eylemlerden birini öneririz:

* uzak araçları Visual Studio çalıştıran farklı bir bilgisayara indirin ve *.exe* dosyasını Windows sunucusuna kopyalayın.

* uzaktan hata ayıklayıcıyı Visual Studio makinenizde [bir dosya paylaşımından](../debugger/remote-debugging.md#fileshare_msvsmon) çalıştırın.

* uzak araçları doğrudan Windows sunucusuna indirin ve güvenilen siteler eklemek için istemleri kabul edin. Modern Web siteleri genellikle birçok üçüncü taraf kaynağı içerir ve bu da birçok istem oluşmasına neden olabilir. Ayrıca, yeniden yönlendirilen bağlantıların el ile eklenmesi gerekebilir. İndirilmeye başlamadan önce bazı güvenilen siteleri eklemeyi tercih edebilirsiniz. **Güvenlik > güvenilen siteler > siteleri > Internet seçenekleri** ' ne gidin ve aşağıdaki siteleri ekleyin.

  * visualstudio.microsoft.com
  * download.visualstudio.microsoft.com
  * hakkında: boş

  My.visualstudio.com üzerindeki hata ayıklayıcının eski sürümleri için, bu diğer siteleri ekleyerek oturum açmanın başarılı olduğundan emin olun:

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

    Uzak araçları indirirken bu etki alanlarını eklemeyi seçerseniz, istendiğinde **Ekle** ' yi seçin.

    ![Engellenen içerik iletişim kutusu](../debugger/media/remotedbg-blocked-content.png)

    Yazılımı indirdiğinizde, çeşitli web sitesi betikleri ve kaynakları yükleme izni vermek için daha fazla istek edinirsiniz. My.visualstudio.com 'de, oturum açma işleminin başarılı olduğundan emin olmak için ek etki alanları eklemenizi öneririz.