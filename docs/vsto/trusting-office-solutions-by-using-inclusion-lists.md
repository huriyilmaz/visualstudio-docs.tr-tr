---
title: Ekleme listelerini kullanarak Office çözümlerine güvenme
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio]
- inclusion lists [Office development in Visual Studio], about inclusion lists
- security [Office development in Visual Studio], inclusion lists
- inclusion lists [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a4787831be31e2f91d668d4e3e7ca91496d7595a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985545"
---
# <a name="trust-office-solutions-by-using-inclusion-lists"></a>Ekleme listelerini kullanarak Office çözümlerine güvenme
  Ekleme listeleri, kullanıcıların yayımcıyı tanımlayan bir sertifikayla imzalanmış Office çözümlerine güven vermesini sağlar. Ekleme listeleri kullanıcıya özeldir ve belge düzeyinde özelleştirmeler ve VSTO eklentileri için kullanılabilirler.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Kullanıcı, bu kullanıcı için güven verilmemiş bir Office çözümünü başlattığında Microsoft Office çözümü, bir güven istemiyle ilgili bir güvenlik kararı ister [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Kullanıcı çözüme güvenmeyi seçerseniz, özelleştirme çalışır ve Kullanıcı bir sonraki sefer istenmez.

## <a name="inclusion-list-and-windows-installer"></a>Ekleme listesi ve Windows Installer
 Windows Installer kullanarak *Program dosyaları* dizinine Office çözümlerini yükleme, yönetici hakları gerektirir. *Program Files* dizinindeki Office çözümleri için, Office çözümlerine zaten FullTrust izni verildiğinden, Office çalışma zamanı Visual Studio Araçları artık ekleme listesini denetlemediğinden.

## <a name="clickonce-trust-prompt"></a>ClickOnce güven istemi
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]Yöneticiler, Office çözümleri için uygulamasını kullanarak, istemek, sorma devre dışı bırakmak veya güvenilir bir sertifika istemek için güven istemi düzeyini yapılandırabilir. Bu yapılandırma, ekleme listesine erişimi denetleyen bir kayıt defteri anahtarı kullanılarak yapılır.

 İstem devre dışıysa, yalnızca güvenilen ve bilinen sertifikaya sahip çözümler yüklenebilir. İstem düzeyi Authenticode gerekli olarak ayarlandıysa, çözüm bilinen bir yetkilinin sertifikası ile imzalanmalıdır, ancak güvenilen bir kök yetkilisine (güvenilen bir sertifika) zincirden bir sertifika gerektirmez. Sorulma izin veriliyorsa, çözüm bilinmeyen kimliğe sahip bir sertifikayla imzalanabilir. Bu senaryoda, güven kararı son kullanıcıya ertelenir ve geçici bir sertifika bir çözümü yüklemek için yeterli olacaktır.

 Daha fazla bilgi için bkz. [nasıl yapılır: ekleme listesi güvenliğini yapılandırma](../vsto/how-to-configure-inclusion-list-security.md) ve tablo 2 ve sorgu kayıt defteri anahtar değeri başlatma etkileri, [ClickOnce güvenilir yayımcıları yapılandırma](/previous-versions/dotnet/articles/ms996418(v=msdn.10)).

## <a name="structure-of-the-inclusion-list"></a>Ekleme listesinin yapısı
 Geçerli bir ekleme listesi girdisi iki bölümden oluşur: dağıtım bildiriminin yolu ve çözümü imzalamak için kullanılan ortak anahtar. Ekleme listesine bir çözüm eklendikten sonra, güvenilir olarak değerlendirilir. Office çözümü çalıştığında, çalışmakta olan çözümün özgün güvenilen sürümle aynı olduğunu doğrulamak için, Office uygulaması ekleme listesindeki ortak anahtarı dağıtım bildiriminde imzalama anahtarıyla karşılaştırır.

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümlerine güven verme](../vsto/granting-trust-to-office-solutions.md)
- [Güvenli Office çözümleri](../vsto/securing-office-solutions.md)
