---
title: Güvenli dağıtım
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c838eddea5b3118c28fb33411a8c58a19d7b4a2d
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810960"
---
# <a name="secure-deployment"></a>Güvenli dağıtım
  Bir Office çözümü oluşturduğunuzda, projenizdeki kodun çalışmasına izin vermek için geliştirme bilgisayarınız otomatik olarak güncelleştirilir. Bununla birlikte, çözümünüzü dağıtırken, çözümü bir sertifikayla imzalayarak veya güven istemi anahtarını kullanarak bir güven kararı temelleyen kanıt sağlamanız gerekir [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Daha fazla bilgi için bkz. [Office çözümlerine güven verme](../vsto/granting-trust-to-office-solutions.md).

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Belge düzeyi özelleştirmeleri için belgeyi bir ağ konumuna dağıtırsanız, belgenin konumunu Office uygulamasının güven merkezindeki güvenilen konumlar listesine de eklemeniz gerekir. Son kullanıcı bilgisayarlarında belge izinlerinin nasıl ayarlanacağı hakkında daha fazla bilgi için bkz. [belgelere güven verme](../vsto/granting-trust-to-documents.md).

## <a name="prevent-office-solutions-from-running-code"></a>Office çözümlerinin kod çalıştırmasını engelle
 Yöneticiler, tüm Office çözümlerinin bir bilgisayarda çalıştırılmasını engellemek için kayıt defterini kullanabilir. Yönetilen kod uzantılarına sahip bir Office çözümü açıldığında, Office çalışma zamanı Visual Studio Araçları, `Disabled` bilgisayardaki aşağıdaki kayıt defteri anahtarlarından biri altında ada sahip bir girdinin olup olmadığını denetler:

- **HKEY_CURRENT_USER \Software\Microsoft\VSTO**

- **HKEY_LOCAL_MACHINE \Software\Microsoft\VSTO**

  Office çözümlerinin kod çalıştırmasını engellemek için, `Disabled` Bu kayıt defteri anahtarlarının bir veya her ikisinde de bir giriş oluşturun ve aşağıdaki veri türlerinden birini ve değerlerini belirtin `Disabled` :

- "0" (sıfır) dışında herhangi bir dizeye ayarlanmış bir REG_SZ veya REG_EXPAND_SZ.

- 0 (sıfır) dışında herhangi bir değere ayarlanmış bir REG_DWORD.

  Office çözümlerini kod çalıştırmaya olanak tanımak için, her iki `Disabled` girdiyi 0 (sıfır) olarak ayarlayın veya kayıt defteri girdilerini silin.

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)
- [Bilgisayarları çalıştırmak veya Office çözümlerini barındırmak için hazırlama](/previous-versions/bb772092(v=vs.110))
- [Güvenli Office çözümleri](../vsto/securing-office-solutions.md)