---
title: ekleme listelerini kullanarak Office çözümlere güven
description: ekleme listelerinin, kullanıcıların yayımcıyı tanımlayan bir sertifikayla imzalanan Office çözümlere güven vermesini sağlama hakkında bilgi edinin.
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: c651a3659d4165d359453df5f64080a2d57b229f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122046262"
---
# <a name="trust-office-solutions-by-using-inclusion-lists"></a>ekleme listelerini kullanarak Office çözümlere güven
  ekleme listeleri, kullanıcıların yayımcıyı tanımlayan bir sertifikayla imzalanan Office çözümlere güven vermesini sağlar. ekleme listeleri kullanıcıya özeldir ve belge düzeyinde özelleştirmeler ve VSTO eklentiler için kullanılabilirler.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 kullanıcı, bu kullanıcı için güven verilmemiş bir Office çözümü başlattığında, Microsoft Office çözüm bir güven istemiyle bir güvenlik kararı ister [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Kullanıcı çözüme güvenmeyi seçerseniz, özelleştirme çalışır ve Kullanıcı bir sonraki sefer istenmez.

## <a name="inclusion-list-and-windows-installer"></a>ekleme listesi ve Windows Installer
 Windows Installer kullanarak *Program dosyaları* dizinine Office çözümleri yükleme, yönetici hakları gerektirir. *Program Files* dizinindeki Office çözümleri için, Office çözümlerine zaten FullTrust izni verildiğinden, Office için Visual Studio Araçları çalışma zamanı ekleme listesini denetlemediğinden artık yoktur.

## <a name="clickonce-trust-prompt"></a>ClickOnce güven istemi
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]yöneticiler, Office çözümleri için uygulamayı kullanarak, istemek, sorma devre dışı bırakmak veya güvenilir bir sertifika istemek için güven istemi düzeyini yapılandırabilir. Bu yapılandırma, ekleme listesine erişimi denetleyen bir kayıt defteri anahtarı kullanılarak yapılır.

 İstem devre dışıysa, yalnızca güvenilen ve bilinen sertifikaya sahip çözümler yüklenebilir. İstem düzeyi Authenticode gerekli olarak ayarlandıysa, çözüm bilinen bir yetkilinin sertifikası ile imzalanmalıdır, ancak güvenilen bir kök yetkilisine (güvenilen bir sertifika) zincirden bir sertifika gerektirmez. Sorulma izin veriliyorsa, çözüm bilinmeyen kimliğe sahip bir sertifikayla imzalanabilir. Bu senaryoda, güven kararı son kullanıcıya ertelenir ve geçici bir sertifika bir çözümü yüklemek için yeterli olacaktır.

 daha fazla bilgi için bkz. [nasıl yapılır: ekleme listesi güvenliğini yapılandırma](../vsto/how-to-configure-inclusion-list-security.md) ve tablo 2, [yapılandırma ClickOnce güvenilen yayımcılar](/previous-versions/dotnet/articles/ms996418(v=msdn.10))içindeki istem düzeyi kayıt defteri anahtar değeri başlatma etkileri.

## <a name="structure-of-the-inclusion-list"></a>Ekleme listesinin yapısı
 Geçerli bir ekleme listesi girdisi iki bölümden oluşur: dağıtım bildiriminin yolu ve çözümü imzalamak için kullanılan ortak anahtar. Ekleme listesine bir çözüm eklendikten sonra, güvenilir olarak değerlendirilir. Office çözümü çalıştığında, Office uygulaması, çalışmakta olan çözümün özgün güvenilen sürümle aynı olduğunu doğrulamak için ekleme listesindeki ortak anahtarı dağıtım bildiriminde imzalama anahtarıyla karşılaştırır.

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümlerine güven verme](../vsto/granting-trust-to-office-solutions.md)
- [Office çözümleri güvenli hale getirme](../vsto/securing-office-solutions.md)
