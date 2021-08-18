---
title: Çözüme güven Office ver
description: Çözüme güven Office, her hedef bilgisayarın güvenlik ilkesinde çözüm derlemesi, dağıtım bildirimi ve belgeye güvenecek şekilde değiştirilmesi anlamına gelir.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: cdf67b8a5cfda899607f0fdca511c78548eb319d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122139848"
---
# <a name="grant-trust-to-office-solutions"></a>Çözüme güven Office ver
  Çözüme güven Office, çözüm derlemesi, uygulama bildirimi, dağıtım bildirimi ve belgeye güvenecek şekilde her hedef bilgisayarın güvenlik ilkesinde değişiklik yapmak anlamına gelir. Siz veya son kullanıcı Office çözümüne güven izni ve olabilir.

 Uygulama ve dağıtım bildirimlerini imzalayarak Office çözümüne tam güven veabilirsiniz.

 Son kullanıcılar, Office isteminde bir güven kararı yaparak çözüme [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] güvenebilir.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trust-the-solution-by-signing-the-application-and-deployment-manifests"></a><a name="Signing"></a> Uygulama ve dağıtım bildirimlerini imzalayarak çözüme güvenin
 Bu çözüme yönelik tüm uygulama Office dağıtım bildirimleri, yayımcıyı tanımlayan bir sertifikayla imzalanmıştır. Sertifikalar güven kararları almak için bir temel sağlar.

 Sizin için geçici bir sertifika oluşturulur ve siz hata ayıklarken çözümün çalışması için derleme zamanında güven izni verildi. Geçici bir sertifikayla imzalanmış bir çözüm yayımlarsanız, son kullanıcıdan güven kararı vermeleri istenir.

 Çözümü bilinen ve güvenilen bir sertifikayla imzalarsanız, son kullanıcıdan güven kararı vermeleri istenmeden çözüm otomatik olarak yüklenir. İmzalama için sertifika alma hakkında daha fazla bilgi için bkz. [ClickOnce ve Authenticode.](../deployment/clickonce-and-authenticode.md) Bir sertifika edindikten sonra sertifikaya Güvenilir Yayımcılar listesine ek olarak açıkça güvenilir olması gerekir. Daha fazla bilgi için, [bkz. How to: Add a trusted publisher to a client computer for ClickOnce.](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)

 Bir geliştirici çözümü geçici bir sertifikayla imzalarsa yönetici, Microsoft .NET Framework araçlarından biri olan Bildirim Oluşturma ve Düzenleme Aracı (*mage.exe)* kullanarak bilinen ve güvenilen bir sertifika ile özelleştirmeyi yeniden imzalar. İmzalama çözümleri hakkında daha fazla bilgi için [bkz. Nasıl Office çözümleri](../vsto/how-to-sign-office-solutions.md) imzalama ve [Nasıl: Uygulama ve dağıtım bildirimlerini imzalama.](../ide/how-to-sign-application-and-deployment-manifests.md)

## <a name="trust-the-solution-by-using-the-clickonce-trust-prompt"></a><a name="TrustPrompt"></a>ClickOnce güven istemini kullanarak çözüme güvenin
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] çözümün sertifikasına güvenen kuruluş genelinde bir ilke yoksa son kullanıcıdan güven kararı vermelerini istenir. Son kullanıcı çözüme güven izni verdiyse, bu güven kararını depolamak için BIR URL ve ortak anahtar içeren bir ekleme listesi girişi oluşturulur. Güvenilen bir özelleştirme daha sonra çalıştırıldı mı, son kullanıcıya bir daha sorulmaz.

 Yöneticiler güven istemini devre dışı bırakabilir veya istemin yalnızca Authenticode sertifikasıyla imzalanmış çözümler [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] için gerçekleşmesini gerekli hale gelebilir. MyComputer, LocalIntranet, Internet, TrustedSites ve UntrustedSites bölgeleri için bu ayarları değiştirme hakkında daha fazla bilgi için, [bkz. Nasıl yapılandırılır: ClickOnce güven](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)istemi davranışını yapılandırma.

## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Office çözümleri](../vsto/securing-office-solutions.md)
- [Belgelere güven izni ver](../vsto/granting-trust-to-documents.md)
- [Çözüm Office sorunlarını giderme](../vsto/troubleshooting-office-solution-security.md)
- [Güvenlik çözümleri için belirli güvenlik Office dikkat edilmesi gerekenler](../vsto/specific-security-considerations-for-office-solutions.md)