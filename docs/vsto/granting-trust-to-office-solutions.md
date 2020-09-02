---
title: Office çözümlerine güven verme
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89315245"
---
# <a name="grant-trust-to-office-solutions"></a>Office çözümlerine güven verme
  Office çözümlerine güven verme, her hedef bilgisayarın güvenlik ilkesini, çözüm derlemesine, uygulama bildirimine, dağıtım bildirimine ve belgeye güvenmek için değiştirme anlamına gelir. Sizin tarafınızdan veya son kullanıcı tarafından Office çözümüne güven verilebilir.

 Uygulama ve dağıtım bildirimlerini imzalayarak Office çözümüne tam güven verebilirsiniz.

 Son kullanıcılar, güven isteminde bir güven kararı sunarak Office çözümüne güven verebilir [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] .

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trust-the-solution-by-signing-the-application-and-deployment-manifests"></a><a name="Signing"></a> Uygulama ve dağıtım bildirimlerini imzalayarak çözüme güvenin
 Office çözümlerine yönelik tüm uygulama ve dağıtım bildirimlerinin yayımcıyı tanımlayan bir sertifikayla imzalanması gerekir. Sertifikalar, güven kararları vermek için bir temel sağlar.

 Sizin için geçici bir sertifika oluşturulur ve derleme zamanında güven verilir, böylece çözüm hata ayıklarken çalışacaktır. Geçici bir sertifikayla imzalanan bir çözüm yayımlarsanız, son kullanıcıdan bir güven kararı yapması istenir.

 Çözümü bilinen ve güvenilen bir sertifikayla imzalayabilirseniz çözüm, son kullanıcıdan bir güven kararı vermesini istemeden otomatik olarak yüklenir. İmzalama için bir sertifika alma hakkında daha fazla bilgi için bkz. [ClickOnce and Authenticode](../deployment/clickonce-and-authenticode.md). Bir sertifika alındıktan sonra, sertifikaya güvenilen yayımcılar listesine eklenerek açık bir şekilde güvenilmelidir. Daha fazla bilgi için bkz. [nasıl yapılır: ClickOnce uygulamaları için bir istemci bilgisayara güvenilir yayımcı ekleme](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).

 Bir geliştirici çözümü geçici bir sertifikayla imzalarsa, yönetici Microsoft .NET Framework araçlarından biri olan Bildirim Oluşturma ve Düzenleme Aracı (*mage.exe*) kullanarak özelleştirmeyi bilinen ve güvenilen bir sertifikayla yeniden imzalayabilirler. Çözümleri imzalama hakkında daha fazla bilgi için bkz. [nasıl yapılır: Office çözümlerini imzalama](../vsto/how-to-sign-office-solutions.md) ve [nasıl yapılır: uygulama ve dağıtım bildirimlerini](../ide/how-to-sign-application-and-deployment-manifests.md)imzalama.

## <a name="trust-the-solution-by-using-the-clickonce-trust-prompt"></a><a name="TrustPrompt"></a>ClickOnce güven istemi 'ni kullanarak çözüme güvenin
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] çözümün sertifikasına güvenen kuruluş genelinde bir ilke yoksa, son kullanıcıdan güven kararı vermesini ister. Son Kullanıcı çözüme güven veriyorsa, bu güven kararını depolamak için bir URL ve ortak anahtar içeren bir ekleme listesi girişi oluşturulur. Güvenilir bir özelleştirme daha sonra çalıştırıldığında son kullanıcıya bir daha istenmez.

 Yöneticiler, güven isteğini devre dışı bırakabilir [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] veya yalnızca bir Authenticode sertifikasıyla imzalanmış çözümler için gerçekleşmesini gerektirebilir. Bu ayarları Bilgisayarım, LocalIntranet, Internet, TrustedSites ve UntrustedSites bölgelerinde değiştirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: ClickOnce güven istemi davranışını yapılandırma](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Office çözümleri](../vsto/securing-office-solutions.md)
- [Belgelere güven verme](../vsto/granting-trust-to-documents.md)
- [Office çözüm güvenliği sorunlarını giderme](../vsto/troubleshooting-office-solution-security.md)
- [Office çözümleri için belirli güvenlik konuları](../vsto/specific-security-considerations-for-office-solutions.md)