---
title: Office çözümlerine güven ihsan edin
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cf7a68d5d3567305e4f70049d76a1c260ddecf25
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303304"
---
# <a name="grant-trust-to-office-solutions"></a>Office çözümlerine güven ihsan edin
  Office çözümlerine güven vermek, çözüm derlemesine, uygulama bildirimine, dağıtım bildirimine ve belgeye güvenecek şekilde her hedef bilgisayarın güvenlik ilkesini değiştirmek anlamına gelir. Güven, Office çözümüne siz veya son kullanıcı tarafından verilebilir.

 Uygulama ve dağıtım bildirimlerini imzalayarak Office çözümüne tam güven verebilirsiniz.

 Son [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] kullanıcılar, güven isteminde güven kararı alarak Office çözümüne güven verebilir.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trust-the-solution-by-signing-the-application-and-deployment-manifests"></a><a name="Signing"></a>Uygulama ve dağıtım bildirimlerini imzalayarak çözüme güvenin
 Office çözümleri için tüm uygulama ve dağıtım bildirimleri yayımcıyı tanımlayan bir sertifikayla imzalanmalıdır. Sertifikalar güven kararları vermek için bir temel sağlar.

 Sizin için geçici bir sertifika oluşturulur ve siz hata ayıklama sırasında çözümün çalışması için yapı zamanında güven verilir. Geçici bir sertifikayla imzalanmış bir çözüm yayımlarsanız, son kullanıcıdan bir güven kararı alınması istenir.

 Çözümü bilinen ve güvenilen bir sertifikayla imzalarsanız, çözüm son kullanıcıdan güven kararı vermesini sormadan otomatik olarak yüklenir. İmzalama için nasıl sertifika alacağıhakkında daha fazla bilgi için [ClickOnce ve Authenticode](../deployment/clickonce-and-authenticode.md)bölümüne bakın. Sertifika alındıktan sonra, sertifikaya Güvenilen Yayıncılar listesine eklenerek açıkça güvenilmesi gerekir. Daha fazla bilgi için [bkz: ClickOnce uygulamaları için istemci bilgisayara güvenilir bir yayımcı ekleyin.](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)

 Bir geliştirici çözümü geçici bir sertifikayla işaretlerse, yönetici Microsoft .NET Framework araçlarından biri olan Bildirim Oluşturma ve Düzenleme Aracı'nı *(mage.exe)* kullanarak bilinen ve güvenilir bir sertifikayla özelleştirmeyi yeniden imzalayabilir. İmzalama çözümleri hakkında daha fazla bilgi için [bkz: Office çözümlerini nasıl imzala](../vsto/how-to-sign-office-solutions.md) ve [nasıl imzala: Uygulama ve dağıtım bildirimlerini imzalayın.](../ide/how-to-sign-application-and-deployment-manifests.md)

## <a name="trust-the-solution-by-using-the-clickonce-trust-prompt"></a><a name="TrustPrompt"></a>ClickOnce güven istemini kullanarak çözüme güvenin
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]çözüm sertifikasına güvenen kuruluş çapında bir ilke yoksa, son kullanıcıdan güven kararını vermesini ister. Son kullanıcı çözüme güven veriyorsa, bu güven kararını depolamak için bir URL ve ortak anahtar içeren bir dahil etme listesi girişi oluşturulur. Güvenilen özelleştirme daha sonra çalıştırıldığında, son kullanıcıdan tekrar istenmez.

 Yöneticiler güven istemini [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] devre dışı kılabilir veya istem'in yalnızca Authenticode sertifikasıyla imzalanan çözümler için oluşmasını isteyebilir. MyComputer, LocalIntranet, Internet, TrustedSites ve UntrustedSites bölgeleri için bu ayarları nasıl değiştireceğiniz hakkında daha fazla bilgi için [bkz.](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Office çözümleri](../vsto/securing-office-solutions.md)
- [Belgelere güven verme](../vsto/granting-trust-to-documents.md)
- [Sorun Giderme Office çözüm güvenliği](../vsto/troubleshooting-office-solution-security.md)
- [Office çözümleri için özel güvenlik konuları](../vsto/specific-security-considerations-for-office-solutions.md)