---
title: Hata Ayıklayıcı Güvenlik | Microsoft Docs
description: Hata ayıklamanın neden olduğu güvenlik risklerini, hem hata ayıklama makinesi hem de hata ayıklama yapılan makineyle ilgili riskleri öğrenin. Riski en aza indirmek için önerileri izleyin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 4b86d0826cc55a7c65a0331e1d136e5af4ee4836
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122154538"
---
# <a name="debugger-security"></a>Hata Ayıklama Güvenliği
Başka bir işlemde hata ayıklama özelliği, özellikle uzaktan hata ayıklarken aksi takdirde sahip olmadığınız son derece geniş güçler sağlar. Kötü amaçlı bir hata ayıklayıcı, hata ayıklanan makinede büyük hasara neden olabilir.

 Ancak birçok geliştirici, güvenlik tehdidinin ters yönde de aksay olduğunun farkında değildir. Hata ayıklama sürecindeki kötü amaçlı kodun hata ayıklama makinesinin güvenliğini tehlikeye atabilir: korunması gereken bir dizi güvenlik açıkları vardır.

## <a name="security-best-practices"></a>En İyi Güvenlik Uygulamaları
 Hata ayıklarken hata ayıkla hata ayıklayıcı arasında örtülü bir güven ilişkisi vardır. Bir şeyin hata ayıklaması yapmak için istekliy olursanız, bunu da çalıştırmaya istekli olursanız. Sonuçta hata ayıklarken güvenebilirsiniz. Güvenemiyorsanız, hata ayıklamamalı veya yalıtılmış bir ortamda tehlikeye atabilecek bir makineden hata ayıklamalısınız.

 Olası saldırı yüzeyini azaltmak için üretim makinelerde hata ayıklama devre dışı bırakılmıştır. Aynı nedenle, hata ayıklama hiçbir zaman süresiz olarak etkinleştirilmez.

### <a name="managed-debugging-security"></a>Yönetilen Hata Ayıklama Güvenliği
 Tüm yönetilen hata ayıklama için geçerli olan bazı genel öneriler burada vetir.

- Güvenilmeyen bir kullanıcının sürecine ekleme yaparken dikkatli olun: bunu yaparken güvenilir olduğunu varsaymış oluruz. Güvenilmeyen bir kullanıcının işlemini eklemeye çalışırken, işleme eklemek isteyip istemediklerini soran bir güvenlik uyarısı iletişim kutusu onay kutusu görüntülenir. "Güvenilen kullanıcılar" sizi ve **aspnet,** **localsystem,** **networkservice** ve **localservice** gibi yüklü .NET Framework makinelerde yaygın olarak tanımlanan standart kullanıcılardır. Daha fazla bilgi için bkz. Güvenlik Uyarısı: Güvenilmeyen bir kullanıcının sahip olduğu bir [işleme ekleme tehlikeli olabilir. Aşağıdaki bilgiler şüpheli görünüyorsa veya emin değilseniz, bu işleme iliştirin.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)

- Bir projeyi İnternet'e indirirken ve içine yüklerken dikkatli [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] olun. Hata ayıklama olmadan bile bunu yapmak çok risklidir. Bunu yapmak için projenin ve içerdiği kodun güvenilir olduğunu varsayabilirsiniz.

  Daha fazla bilgi için bkz. [Yönetilen Kodda Hata Ayıklama.](../debugger/debugging-managed-code.md)

### <a name="remote-debugging-security"></a>Uzaktan Hata Ayıklama Güvenliği
 Yerel hata ayıklama genellikle uzaktan hata ayıklamadan daha güvenlidir. Uzaktan hata ayıklama, yoklama için toplam yüzey alanı artırır.

 Bu Visual Studio Uzaktan Hata Ayıklama İzleyicisi (msvsmon.exe) uzaktan hata ayıklamada kullanılır ve yapılandırmaya çeşitli güvenlik önerileri vardır. Kimlik doğrulama modunu yapılandırmanın tercih edilen yolu, Windows Kimlik Doğrulaması yok modu güvenli değildir.

 ![Hata iletişim kutusu](../debugger/media/dbg_err_remotepermissionschanged.png "DBG_ERR_RemotePermissionsChanged")

 Windows Kimlik Doğrulaması modunu kullanırken, güvenilmeyen bir kullanıcıya msvsmon'a bağlanma izni verilmesinin tehlikeli olduğunu, çünkü kullanıcıya msvsmon'ı barındıran bilgisayarda tüm izinlerinizi verilmesinin tehlikeli olduğunu farkında olun.

 Uzak makinede bilinmeyen bir işlemde hata ayıklamayın: Hata ayıklayıcıyı çalıştıran makineyi etkileyebilecek veya msvsmon'ın güvenliğini tehlikeye atan olası güvenlik açıkları olabilir. Bilinmeyen bir işlemde kesinlikle hata ayıklamanız gerekirse, yerel olarak hata ayıklamayı deneyin ve olası tehditleri yerelleştirilmiş olarak tutmak için bir güvenlik duvarı kullanın.

 msvsmon'ı yapılandırma hakkında bilgi için [bkz. Uzaktan hata ayıklayıcıyı ayarlama.](../debugger/remote-debugging.md#bkmk_setup)

### <a name="web-services-debugging-security"></a>Web Hizmetleri Hata Ayıklama Güvenliği
 Yerel olarak hata ayıklamak daha güvenlidir, ancak büyük olasılıkla web sunucusuna yüklememiş olabileceğiniz için yerel hata [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ayıklama pratik olmayacaktır. Genel olarak, Web hizmetlerde hata ayıklama, geliştirme dışında uzaktan yapılır, bu nedenle uzaktan hata ayıklama güvenliği için öneriler Web hizmetleri hata ayıklaması için de geçerlidir. İşte bazı ek en iyi yöntemler. Daha fazla bilgi için [bkz. XML Web Hizmetleri'ne Hata Ayıklama.](/previous-versions/ms241873(v=vs.100))

- Güvenliği tehlikeye atılmış bir Web sunucusunda hata ayıklamayı etkinleştirme.

- Hata ayıklamadan önce Web sunucusunun güvenli olduğundan emin olun. Güvenli olduğundan emin değilsanız hata ayıklamayın.

- İnternet'e açık bir Web hizmetinde hata ayıklarken özellikle dikkatli olun.

### <a name="external-components"></a>Dış Bileşenler
 Özellikle kodu yazmadıysanız, programla etkileşimde bulunan dış bileşenlerin güven durumunun farkında olmak. Ayrıca veya hata [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ayıklayıcının kullanabileceği bileşenlere de dikkat.

### <a name="symbols-and-source-code"></a>Semboller ve Kaynak Kodu
 Güvenlik [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] hakkında düşünme gerektiren iki araç aşağıdakilerdir:

- Kaynak kod deposundaki kaynak kodu sürümlerini sağlayan Kaynak Sunucu. Bir programın kaynak kodunun geçerli sürümüne sahip değilken kullanışlıdır. [Güvenlik Uyarısı: Hata Ayıklayıcısı Güvenilmeyen Komutu Yürütmeli.](../debugger/security-warning-debugger-must-execute-untrusted-command.md)

- Sistem çağrısı sırasında kilitlenmede hata ayıklamak için gereken sembolleri sağlamak için kullanılan Sembol Sunucusu.

  Bkz. [Sembol Belirtme (.pdb) ve Kaynak Dosyaları](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklayıcısı Ayarlar Hazırlama](../debugger/debugger-settings-and-preparation.md)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [Güvenlik Uyarısı: Güvenilmeyen bir kullanıcının sahip olduğu bir işleme ekleme tehlikeli olabilir. Aşağıdaki bilgiler şüpheli görünüyorsa veya emin değilseniz bu işleme ekleme](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
- [Güvenlik Uyarısı: Hata Ayıklayıcı Güvenilmeyen Komut Yürütmeli](../debugger/security-warning-debugger-must-execute-untrusted-command.md)