---
title: Güvenli dağıtım
description: Çözümü bir sertifikayla imzalayarak veya güvenlik istemi anahtarını kullanarak güven kararına temel ClickOnce sağlamanız gerektiğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio], security
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- ClickOnce deployment [Office development in Visual Studio], security
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: df241aa2a2f67b18d11653ba016b39b561866bec
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122025751"
---
# <a name="secure-deployment"></a>Güvenli dağıtım
  Yeni bir çözüm Office, geliştirme bilgisayarınız projenizin kodunun çalışmasına izin verecek şekilde otomatik olarak güncelleştirilir. Ancak, çözümlerinizi dağıtırken, çözümü bir sertifikayla imzalayarak veya güven istemi anahtarını kullanarak güven kararını temel alan bir kanıt [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] sağlanız gerekir. Daha fazla bilgi için, [bkz. Grant trust to Office solutions](../vsto/granting-trust-to-office-solutions.md).

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Belge düzeyinde özelleştirmeler için, belgeyi bir ağ konuma dağıtırsanız, belgenin konumunu, belge uygulamanın Güven Merkezi'nde güvenilir konumlar listesine de Office gerekir. Son kullanıcı bilgisayarlarında belge izinlerini ayarlama hakkında daha fazla bilgi için bkz. [Belgelere güven izni ver.](../vsto/granting-trust-to-documents.md)

## <a name="prevent-office-solutions-from-running-code"></a>Çözüm Office çalıştırmasını engelleme
 Yöneticiler kayıt defterini kullanarak tüm Office çözümlerinin bilgisayarda çalışmasını önlenebilir. Yönetilen Office olan bir çözüm açıldığında, Office için Visual Studio Araçları çalışma zamanı bilgisayarda aşağıdaki kayıt defteri anahtarlarından biri altında adı olan bir girişin var olup `Disabled` olmadığını denetler:

- **HKEY_CURRENT_USER\Software\Microsoft\VSTO**

- **HKEY_LOCAL_MACHINE\Software\Microsoft\VSTO**

  Bu Office çalıştırmasını önlemek için, bu kayıt defteri anahtarlarından biri veya her ikisi altında bir giriş oluşturun ve için aşağıdaki veri türlerinden ve `Disabled` değerlerinden birini `Disabled` belirtin:

- "0 REG_SZ (REG_EXPAND_SZ) dışında herhangi bir dizeye ayarlanmış bir dize veya dize.

- 0 REG_DWORD (sıfır) dışında herhangi bir değere ayarlanmış bir değerdir.

  Bu Office kod çalıştırmaya olanak sağlamak için her iki girdiyi de 0 (sıfır) olarak ayarlayın `Disabled` veya kayıt defteri girdilerini silin.

## <a name="see-also"></a>Ayrıca bkz.
- [Bir Office dağıtma](../vsto/deploying-an-office-solution.md)
- [Bilgisayarları farklı çözümleri çalıştırmaya veya barındırmaya Office hazırlama](/previous-versions/bb772092(v=vs.110))
- [Güvenli Office çözümleri](../vsto/securing-office-solutions.md)