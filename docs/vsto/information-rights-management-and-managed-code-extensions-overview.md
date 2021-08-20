---
title: Bilgi hakları yönetimi & kod uzantıları
description: Yetkisiz kişilerin hassas Rights Management görüntülemesini veya değiştirmesini önlemeye yardımcı olan Information Rights Management (IRM) hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Information Rights Management [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- IRM [Office development in Visual Studio]
- documents [Office development in Visual Studio], restricted permissions
- rights management [Office development in Visual Studio]
- Office documents [Office development in Visual Studio, restricted permissions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: fb32bc23de2335a912d1f2f6d3047af140961404
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147908"
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>Bilgi hakları yönetimi ve yönetilen kod uzantılarına genel bakış
  Microsoft Office Word ve Microsoft Office Excel, yetkisiz Rights Management hassas bilgileri görüntülemesini veya değiştirmesini önlemeye yardımcı olan Information Rights Management (IRM) özelliği sağlar. Information Rights Management'nin nasıl Rights Management için belirli bir uygulamanın yardım Office bakın.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="run-code-behind-documents-with-restricted-permissions"></a>Kısıtlı izinlere sahip belgelerin arkasında kod çalıştırma
 Çözümünüz IRM kullanan bir belge veya çalışma kitabı içeriyorsa, varsayılan olarak Word Excel kod çalıştırmaya izin vermez. Belgenin yazarı siz veya Tam Denetim erişiminiz varsa, çözümünüz için varsayılan ayarı değiştirebilirsiniz. Daha fazla bilgi için [bkz. Nasıl kullanılır: Kodun kısıtlı izinlere sahip belgelerin arkasında çalışmasına izin verme.](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)

 IRM, belgede <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> önbelleğe alınan verileri almak veya işlemek için kullanımını önler.

## <a name="end-users-to-restrict-permissions-to-documents-that-use-managed-code-extensions"></a>İzinleri yönetilen kod uzantıları kullanan belgelerle kısıtlamak için son kullanıcılar
 Çözümünüzde belgeye veya çalışma kitabına Tam Denetim erişimi olan herkes izinleri kısıtlamak için IRM kullanabilir. Örneğin, muhasebe departmanında son kullanıcı çalışma sayfasını bir veritabanındaki verilerle otomatik olarak doldurmak için bir çözüm kullanıyorsa, bu kullanıcı yalnızca kendi departmanında olan kullanıcılara Değişiklik erişimi ve Başkalarına Okuma erişimi vermek istiyor olabilir. Kullanıcı kısıtlanmış izinleri eklerken varsayılan olarak çalışma sayfasının arkasındaki kod çalıştıramaz ve çalışma sayfası verilerle doldurulamaz.

 Sorunu çözmek için belgeye veya çalışma kitabına Tam Denetim erişimi olan birinin nesne modeline programlı erişime izin vermek için varsayılan izin ayarlarını değiştirmesi gerekir. Daha fazla bilgi için [bkz. Nasıl kullanılır: Kodun kısıtlı izinlere sahip belgelerin arkasında çalışmasına izin verme.](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Belge düzeyi çözümlerde belge koruması](../vsto/document-protection-in-document-level-solutions.md)
- [Office belgelerde parola koruması](../vsto/password-protection-on-office-documents.md)
- [Güvenli Office çözümleri](../vsto/securing-office-solutions.md)
- [Bir Office dağıtma](../vsto/deploying-an-office-solution.md)
- [Yeni çözümler tasarlama Office oluşturma](../vsto/designing-and-creating-office-solutions.md)
