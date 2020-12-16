---
title: Ekleme listelerini kullanarak Office çözümlerine güvenme
description: Ekleme listelerinin, kullanıcıların yayımcıyı tanımlayan bir sertifikayla imzalanmış Office çözümlerine güven vermesini sağlama hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 3bb5c111b4c75298ee55bc64dfbb2d0dd4b6c8b5
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527469"
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
