---
title: Hata ayıklayıcı güvenliği | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], security
- debugger, security
- security [Visual Studio], debugging best practices
ms.assetid: d4fc3c43-e844-419c-8dbb-551cc2a9b09e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a89e60a47e5bab6580c78275357234bb9d3f1c56
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80527922"
---
# <a name="debugger-security"></a>Hata Ayıklama Güvenliği
Başka bir işlemde hata ayıklama özelliği, özellikle de uzaktan hata ayıklarken, daha önce sahip olmamanıza izin veren son derece geniş bir üstür sağlar. Kötü amaçlı bir hata ayıklayıcı, hata ayıklanan makinede yaygın olarak hasar verebilir.

 Ancak birçok geliştirici, güvenlik tehdidi 'nın ters yönde de akabileceğini fark etmez. Hata ayıklanan işlemdeki kötü amaçlı kod, hata ayıklama makinesinin güvenliğini tehlikeye atacağından, buna karşı korunması gereken bir dizi güvenlik açığından daha vardır.

## <a name="security-best-practices"></a>En İyi Güvenlik Uygulamaları
 Hata ayıkladığınız kod ile hata ayıklayıcı arasında örtülü bir güven ilişkisi vardır. Bir hata ayıklama yapmak istiyorsanız, onu da çalıştırmak isteyebilirsiniz. En alttaki satır, hata ayıkladıklarınızı güvenebilmeniz gerekir. Bu güvene güvenmiyorsanız, bu durumda hata ayıklamalısınız veya bir yalıtılmış ortamda, bu durumda hata ayıklamalı veya bir bilgisayardan hata ayıklaması yapmalısınız.

 Olası saldırı yüzeyini azaltmak için, üretim makinelerinde hata ayıklama devre dışı bırakılmalıdır. Aynı nedenden dolayı, hata ayıklama asla süresiz olarak etkinleştirilmemelidir.

### <a name="managed-debugging-security"></a>Yönetilen hata ayıklama güvenliği
 Tüm yönetilen hata ayıklama için uygulanan bazı genel öneriler aşağıda verilmiştir.

- Güvenilmeyen bir kullanıcının işlemine eklenirken dikkatli olun: Bunu yaptığınızda, güvenilir olduğunu varsayabilirsiniz. Güvenilmeyen bir kullanıcının sürecine iliştirmeye çalıştığınızda, işleme eklemek isteyip istemediğinizi soran bir güvenlik uyarısı iletişim kutusu onayı görüntülenir. "Güvenilen kullanıcılar" size ve **ASPNET**, **LocalSystem**, **NetworkService**ve **LocalService**gibi .NET Framework yüklü makinelerde yaygın olarak tanımlanmış bir dizi standart Kullanıcı içerir. Daha fazla bilgi için bkz [. güvenlik uyarısı: güvenilmeyen bir kullanıcının sahip olduğu bir Işleme ekleme tehlikeli olabilir. Aşağıdaki bilgiler şüpheli görünüyorsa veya emin değilseniz, bu işleme](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)eklemeyin.

- Bir projeyi Internet 'ten indirirken ve içine yüklerken dikkatli olun [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Hata ayıklama olmadan bile bu çok riskli olur. Bunu yaptığınızda, projenin ve içerdiği kodun güvenilir olduğunu varsayıyoruz.

  Daha fazla bilgi için bkz. [yönetilen kodda hata ayıklama](../debugger/debugging-managed-code.md).

### <a name="remote-debugging-security"></a>Uzaktan hata ayıklama güvenliği
 Yerel hata ayıklama genellikle uzaktan hata ayıklamadan daha güvenlidir. Uzaktan hata ayıklama, araştırılan toplam yüzey alanını arttırır.

 Visual Studio Uzaktan Hata Ayıklama İzleyicisi (msvsmon.exe) uzaktan hata ayıklamada kullanılır ve bu yapılandırmayı yapılandırmaya yönelik birkaç güvenlik önerisi vardır. Kimlik doğrulama modu güvensiz olmadığından, kimlik doğrulama modunu yapılandırmanın tercih edilen yolu Windows kimlik doğrulamadır.

 ![Hata iletişim kutusu](../debugger/media/dbg_err_remotepermissionschanged.png "DBG_ERR_RemotePermissionsChanged")

 Windows kimlik doğrulama modu kullanırken, kullanıcıya msvsmon 'yi barındıran bilgisayarda tüm izinleriniz verildiğinden, güvenilir olmayan bir kullanıcıya msvsmon 'e bağlanma izni verilmesinin tehlikeli olduğunu unutmayın.

 Uzak makinedeki bilinmeyen bir işlemde hata ayıklama: hata ayıklayıcıyı çalıştıran makineyi etkileyebilecek veya msvsmon tehlikeye atabilecek potansiyel yazılımlar vardır. Kesin olarak bilinmeyen bir işlemde hata ayıklaması yapmanız gerekiyorsa, yerel olarak hata ayıklamayı deneyin ve olası tehditleri yerelleşmiş tutmak için bir güvenlik duvarı kullanın.

 Msvsmon yapılandırma hakkında daha fazla bilgi için bkz. [Uzaktan hata ayıklayıcıyı ayarlama](../debugger/remote-debugging.md#bkmk_setup).

### <a name="web-services-debugging-security"></a>Web Hizmetleri hata ayıklama güvenliği
 Yerel olarak hata ayıklamak daha güvenlidir, ancak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Web sunucusunda yüklü olmadığından, yerel hata ayıklama pratik olmayabilir. Genellikle, Web hizmetlerinde hata ayıklama geliştirme sırasında uzaktan yapılır, bu nedenle uzaktan hata ayıklama güvenliği için öneriler Web Hizmetleri hata ayıklaması için de geçerlidir. İşte bazı ek en iyi yöntemler. Daha fazla bilgi için bkz. [XML Web hizmetlerinde hata ayıklama](https://msdn.microsoft.com/library/c900b137-9fbd-4f59-91b5-9c2c6ce06f00).

- Güvenliği aşılmış bir Web sunucusunda hata ayıklamayı etkinleştirmeyin.

- Hata ayıklamadan önce Web sunucusunun güvenli olduğundan emin olun. Güvenli olduğundan emin değilseniz, hata ayıklamayın.

- Özellikle de Internet üzerinde sunulan bir Web hizmetinde hata ayıklaması yapıyorsanız dikkatli olun.

### <a name="external-components"></a>Dış bileşenler
 Özellikle kodu yazmadınız, programınızın etkileşimde bulunduğu dış bileşenlerin güven durumunu unutmayın. Ayrıca [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , veya hata ayıklayıcının kullanabileceği bileşenlere de dikkat edin.

### <a name="symbols-and-source-code"></a>Semboller ve kaynak kodu
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Güvenlik hakkında düşünce gerektiren iki araç şunlardır:

- Kaynak sunucu, kaynak kod deposundan kaynak kodu sürümleri sağlar. Bir programın kaynak kodunun güncel sürümüne sahip değilseniz yararlıdır. [Güvenlik uyarısı: hata ayıklayıcı güvenilmeyen komut yürütmelidir](../debugger/security-warning-debugger-must-execute-untrusted-command.md).

- Bir sistem çağrısı sırasında çökmeye hata ayıklamak için gereken sembolleri sağlamak için kullanılan sembol sunucusu.

  Bkz [. simge (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklayıcısı Ayarları ve Hazırlığı](../debugger/debugger-settings-and-preparation.md)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [Güvenlik Uyarısı: güvenilmeyen bir kullanıcının sahip olduğu bir işleme ekleme tehlikeli olabilir. Aşağıdaki bilgiler şüpheli görünüyorsa veya emin değilseniz, bu işleme eklemeyin](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
- [Güvenlik Uyarısı: hata ayıklayıcı güvenilmeyen komut yürütmelidir](../debugger/security-warning-debugger-must-execute-untrusted-command.md)