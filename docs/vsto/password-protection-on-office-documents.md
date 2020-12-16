---
title: Office belgelerinde parola koruması
description: Microsoft Word belgeleriniz ve Excel çalışma kitaplarında, yetkisiz kullanıcılar tarafından açılabilmeleri için bir parola ayarlamayı öğrenin.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b6beaf85000438846e5d440e48c9722b9660f9bd
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528069"
---
# <a name="password-protection-on-office-documents"></a>Office belgelerinde parola koruması
  Microsoft Office Word belgelerinizi ve Microsoft Office Excel çalışma kitaplarını, parolayı kullanmayan birisi tarafından açılabilmeleri için bir parola ayarlamak mümkündür. Bu seçeneğe **açık parola** adı verilir.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 **Açık etkin üzerinde parola** bulunan mevcut belge ve çalışma kitaplarını kullanarak belge düzeyinde projeler oluşturabilirsiniz. Visual Studio 'daki davranış, **açık etkin parolası** olan Word ve Excel belgeleri için farklıdır.

 **Açık parola** etkinleştirme hakkında daha fazla bilgi için bkz. Word veya Excel 'de yardım.

## <a name="behavior-of-excel-and-word"></a>Excel ve Word davranışı
 Visual Studio 'da **açık etkin parola** bulunan bir Excel çalışma kitabını her açışınızda, Excel sizden parolayı ister. Çözümünüzü oluştururken, belge derleme sırasında açıldığından parolayı yeniden girmeniz istenir.

 Visual Studio 'da **açık etkin parolanın** bulunduğu bir Word belgesini ilk açışınızda, Word sizden parolayı ister. Parolayı başarıyla girdikten sonra, açma ile **Ilgili parola** belgeden kaldırılır ve belgeyi açmak artık bir parola gerektirmeyecektir. Çözümünüzdeki belgenin açılabilmesi için parola gerektirmesini istiyorsanız, son derlemenize ve çözümü dağıtmadan önce **Açık olarak parolayı** etkinleştirmeniz gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Belge düzeyi çözümlerde Belge koruması](../vsto/document-protection-in-document-level-solutions.md)
- [Bilgi hakları yönetimine ve yönetilen kod uzantılarına genel bakış](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Nasıl yapılır: kodun, kısıtlı izinlerle belgelerin arkasında çalışmasına Izin verme](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md)
