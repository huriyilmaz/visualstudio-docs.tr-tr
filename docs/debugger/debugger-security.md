---
title: Hata Ayıklama Güvenliği | Microsoft Dokümanlar
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
ms.sourcegitcommit: 334024a43477290ecc610e70c80a0f772787a7d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80527922"
---
# <a name="debugger-security"></a>Hata Ayıklama Güvenliği
Başka bir işlemi hata ayıklama yeteneği, özellikle uzaktan hata ayıklama, aksi takdirde olmazdı son derece geniş güçler verir. Kötü niyetli bir hata ayıklama makinesi nin debugged olan yaygın hasar verebilir.

 Ancak, birçok geliştirici güvenlik tehdidi de ters yönde akabilir farkında değildir. Hata ayıklama işlemindeki kötü amaçlı kodların hata ayıklama makinesinin güvenliğini tehlikeye atması mümkündür: korunması gereken bir dizi güvenlik açıkları vardır.

## <a name="security-best-practices"></a>En İyi Güvenlik Uygulamaları
 Hata ayıklama kod ve hata ayıklayıcı arasında örtülü bir güven ilişkisi vardır. Bir şeyi hata ayıklamak istiyorsanız, onu çalıştırmak için de istekli olmalısınız. Alt satırda, hata ayıklama ne güvenebilmek gerekir. Ona güvenemiyorsanız, hata ayıklamamalısınız veya tehlikeye atabileceğiniz bir makineden ve yalıtılmış bir ortamda hata ayıklamanız gerekir.

 Olası saldırı yüzeyini azaltmak için, üretim makinelerinde hata ayıklama devre dışı edilmelidir. Aynı nedenle, hata ayıklama süresiz olarak etkinleştirilmemelidir.

### <a name="managed-debugging-security"></a>Yönetilen Hata Ayıklama Güvenliği
 Yönetilen tüm hata ayıklama için geçerli olan bazı genel öneriler aşağıda veda edinilir.

- Güvenilmeyen bir kullanıcının işlemine iliştirirken dikkatli olun: Bunu yaptığınızda güvenilir olduğunu varsaymış olursunuz. Güvenilmeyen bir kullanıcının işlemine eklemeye çalıştığınızda, işleme eklemek isteyip istemediğiniz soran bir güvenlik uyarı iletişim kutusu onayı görüntülenir. "Güvenilen kullanıcılar" sizi ve .NET Framework yüklü olan makinelerde yaygın olarak tanımlanan **aspnet,** **localsystem,** **networkservice**ve **localservice**gibi standart kullanıcıları içerir. Daha fazla bilgi için [bkz: Güvenlik Uyarısı: Güvenilmeyen bir kullanıcıya ait bir işleme bağlanmak tehlikeli olabilir. Aşağıdaki bilgiler şüpheli görünüyorsa veya emin değilseniz, bu işleme eklemeyin.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)

- Bir projeyi Internet'ten indirirken ve [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]'ye yüklerken dikkatli olun. Bu hata ayıklama olmadan bile yapmak çok risklidir. Bunu yaptığınızda, projenin ve içerdiği kodun güvenilir olduğunu varsayabilirsiniz.

  Daha fazla bilgi için Bkz. [Hata Ayıklama Yönetilen Kod.](../debugger/debugging-managed-code.md)

### <a name="remote-debugging-security"></a>Uzaktan Hata Ayıklama Güvenliği
 Yerel hata ayıklama genellikle uzaktan hata ayıklama daha güvenlidir. Uzaktan hata ayıklama, incelenebilecek toplam yüzey alanını artırır.

 Visual Studio Uzaktan Hata Ayıklama Monitörü (msvsmon.exe) uzaktan hata ayıklamada kullanılır ve yapılandırmak için çeşitli güvenlik önerileri vardır. Kimlik doğrulama modunu yapılandırmanın tercih edilen yolu, Kimlik Doğrulama modu güvenli olmadığından Windows Kimlik Doğrulama'dır.

 ![Hata iletişim kutusu](../debugger/media/dbg_err_remotepermissionschanged.png "DBG_ERR_RemotePermissionsChanged")

 Windows Kimlik Doğrulama modunu kullanırken, msvsmon'a bağlanmak için güvenilmeyen bir kullanıcıya izin vermenin tehlikeli olduğunu unutmayın, çünkü kullanıcıya msvsmon barındıran bilgisayardaki tüm izinleriniz verilir.

 Uzak bir makinede bilinmeyen bir işlemi hata ayıklama: hata ayıklayıcıyı çalıştıran makineyi etkileyebilecek veya msvsmon'u tehlikeye atabilecek olası açıklar vardır. Bilinmeyen bir işlemi kesinlikle hata ayıklamanız gerekiyorsa, yerel olarak hata ayıklamayı deneyin ve olası tehditleri yerelleştirmiş tutmak için bir güvenlik duvarı kullanın.

 msvsmon yapılandırma hakkında bilgi için [bkz.](../debugger/remote-debugging.md#bkmk_setup)

### <a name="web-services-debugging-security"></a>Web Hizmetleri Hata Ayıklama Güvenliği
 Yerel hata ayıklama daha güvenlidir, ancak büyük [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] olasılıkla web sunucusunda yüklü değil, yerel hata ayıklama pratik olmayabilir. Genellikle, Web hizmetlerinin hata ayıklama geliştirme sırasında dışında uzaktan yapılır, bu nedenle uzaktan hata ayıklama güvenliği için öneriler web hizmetleri hata ayıklama için de geçerlidir. Aşağıda bazı ek en iyi uygulamalar veremistir. Daha fazla bilgi için Bkz. [Hata Ayıklama XML Web Hizmetleri.](https://msdn.microsoft.com/library/c900b137-9fbd-4f59-91b5-9c2c6ce06f00)

- Gizliliği ihlal edilmiş bir Web sunucusunda hata ayıklamayı etkinleştirme.

- Hata ayıklamadan önce Web sunucusunun güvenli olduğundan emin olun. Güvenli olduğundan emin değilseniz, hata ayıklama.

- Internet'te açıkta olan bir Web hizmetini hata ayıklıyorsanız özellikle dikkatli olun.

### <a name="external-components"></a>Dış Bileşenler
 Özellikle kodu yazmadıysanız, programınızın etkileşimde olduğu dış bileşenlerin güven durumuna dikkat edin. Ayrıca, hata ayıklayıcının kullanabileceği bileşenlerden [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] de haberdar olun.

### <a name="symbols-and-source-code"></a>Semboller ve Kaynak Kodu
 Güvenlik [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] hakkında düşünmeyi gerektiren iki araç şunlardır:

- Kaynak Kodu deposundan kaynak kodu sürümlerini sağlayan Kaynak Sunucu. Bir programın kaynak kodunun geçerli sürümüyoksa yararlıdır. [Güvenlik Uyarısı: Hata Ayıklama Güvenilmeyen Komutu Yürütmelidir.](../debugger/security-warning-debugger-must-execute-untrusted-command.md)

- Sembol Sunucusu, sistem çağrısı sırasında bir kilitlenme hata ayıklamak için gerekli sembolleri sağlamak için kullanılır.

  Bkz. [Simge belirt (.pdb) ve Kaynak Dosyaları](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklama Ayarları ve Hazırlama](../debugger/debugger-settings-and-preparation.md)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [Güvenlik Uyarısı: Güvenilmeyen bir kullanıcıya ait bir işleme bağlanmak tehlikeli olabilir. Aşağıdaki bilgiler şüpheli görünüyorsa veya emin değilseniz, bu işleme eklemeyin](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
- [Güvenlik Uyarısı: Hata Ayıklama Güvenilmeyen Komutu Yürütmeli](../debugger/security-warning-debugger-must-execute-untrusted-command.md)