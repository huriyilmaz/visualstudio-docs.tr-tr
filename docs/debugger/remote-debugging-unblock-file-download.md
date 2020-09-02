---
title: Uzak Araçlar indirmenin engellemesini kaldır
ms.date: 07/19/2018
ms.topic: troubleshooting
helpviewer_keywords:
- remote debugging, unblock download
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a243033bf5831952d83fdf688302651e02b76b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62903036"
---
# <a name="how-to-unblock-the-download-of-the-remote-tools-on-windows-server"></a>Nasıl yapılır: Windows Server 'da uzak araçların indirilmesini kaldırma

Windows Server 'da Internet Explorer 'daki varsayılan güvenlik ayarları, uzak Araçlar gibi bileşenlerin indirileceği zaman alıcı olabilir.

* Gelişmiş güvenlik yapılandırması, Internet Explorer 'da etkinleştirilir ve bu da, kaynağı içeren etki alanına açıkça izin verilmediği (yani, güvenilen) Web sitelerini açmanızı ve Web kaynaklarına erişmenizi önler. Bu ayarı devre dışı bırakabilseniz de, bir güvenlik riski sunabileceğinden bunu önermiyoruz.

* Windows Server 2016 ' de, **Internet seçenekleri**  >  **güvenliği**  >  **Internet**  >  **özel düzeyi**  >  **indirmelerinde** varsayılan ayar dosya indirmelerini devre dışı bırakır. Uzak araçları doğrudan Windows Server 'a indirmeyi seçerseniz, dosya indirmeyi etkinleştirmelisiniz.

Araçları Windows Server 'a indirmek için aşağıdakilerden birini öneririz:

* Uzak araçları, Visual Studio çalıştıran bir bilgisayar gibi farklı bir bilgisayara indirin ve ardından *. exe* dosyasını Windows Server 'a kopyalayın.

* Uzaktan hata ayıklayıcıyı Visual Studio makinenizde [bir dosya paylaşımından](../debugger/remote-debugging.md#fileshare_msvsmon) çalıştırın.

* Uzak araçları doğrudan Windows Server 'a indirin ve güvenilen siteler eklemek için istemleri kabul edin. Modern Web siteleri çoğunlukla birçok üçüncü taraf kaynağı içerir, bu nedenle bu çok sayıda istem oluşmasına neden olabilir. Ayrıca, yeniden yönlendirilen bağlantıların el ile eklenmesi gerekebilir. İndirilmeye başlamadan önce bazı güvenilen siteleri eklemeyi tercih edebilirsiniz. **Güvenlik > güvenilen siteler > siteleri > Internet seçenekleri** ' ne gidin ve aşağıdaki siteleri ekleyin.

  * visualstudio.microsoft.com
  * download.visualstudio.microsoft.com
  * hakkında: boş

  My.visualstudio.com üzerindeki hata ayıklayıcının eski sürümleri için, oturum açmanın başarılı olduğundan emin olmak için bu ek siteleri ekleyin:

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

    Yazılımı indirdiğinizde, çeşitli web sitesi betikleri ve kaynakları yüklemeye izin vermek için bazı ek istekler alırsınız. My.visualstudio.com 'de, oturum açma işleminin başarılı olduğundan emin olmak için ek etki alanları eklemenizi öneririz.