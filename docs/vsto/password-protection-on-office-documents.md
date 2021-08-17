---
title: Office belgelerde parola koruması
description: Microsoft Word belgelerinizde bir parola ayarlamayı ve Excel çalışma kitaplarını yetkisiz kullanıcılar tarafından açılabilmeleri için nasıl ayarlayacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- passwords [Office development in Visual Studio], document protections
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 80e89d5907fca8d4896ba0349bf26b527c11b1cd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122099613"
---
# <a name="password-protection-on-office-documents"></a>Office belgelerde parola koruması
  Microsoft Office Word belgelerinizi ve Microsoft Office Excel çalışma kitaplarını, parolayı kullanmayan birisi tarafından açılabilmeleri için bir parola ayarlamak mümkündür. Bu seçeneğe **açık parola** adı verilir.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 **Açık etkin üzerinde parola** bulunan mevcut belge ve çalışma kitaplarını kullanarak belge düzeyinde projeler oluşturabilirsiniz. Visual Studio davranışı, **açık etkin parolası** olan Word ve Excel belgeleri için farklıdır.

 **Açık parolanın** etkinleştirilmesi hakkında daha fazla bilgi için bkz. Word veya Excel Yardım.

## <a name="behavior-of-excel-and-word"></a>Excel ve Word davranışı
 **açık etkin parola** olan Visual Studio Excel çalışma kitabını her açışınızda Excel parolanızı ister. Çözümünüzü oluştururken, belge derleme sırasında açıldığından parolayı yeniden girmeniz istenir.

 **açık etkin parolanın** bulunduğu Visual Studio bir word belgesini ilk açışınızda, word sizden parolayı ister. Parolayı başarıyla girdikten sonra, açma ile **Ilgili parola** belgeden kaldırılır ve belgeyi açmak artık bir parola gerektirmeyecektir. Çözümünüzdeki belgenin açılabilmesi için parola gerektirmesini istiyorsanız, son derlemenize ve çözümü dağıtmadan önce **Açık olarak parolayı** etkinleştirmeniz gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Belge düzeyi çözümlerde Belge koruması](../vsto/document-protection-in-document-level-solutions.md)
- [Bilgi hakları yönetimine ve yönetilen kod uzantılarına genel bakış](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Nasıl yapılır: kodun, kısıtlı izinlerle belgelerin arkasında çalışmasına Izin verme](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md)
