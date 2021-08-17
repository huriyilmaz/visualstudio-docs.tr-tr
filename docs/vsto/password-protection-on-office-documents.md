---
title: Office belgelerde parola koruması
description: Yetkisiz kullanıcıların açmasını engellemek için Microsoft Word ve Excel çalışma kitaplarında parola ayarlamayı öğrenin.
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
ms.openlocfilehash: a785eab3856a9d25e5dd8d620fd56ff7c5a8455494bfd60f00f077c490b2bf1e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121394114"
---
# <a name="password-protection-on-office-documents"></a>Office belgelerde parola koruması
  Microsoft Office Word belgelerinize ve Microsoft Office Excel çalışma kitaplarınızı parolayı bilmiyorsanız açamazsınız. Bu seçenek Açıkken **Parola olarak adlandırılan bir seçenektir.**

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Açık parolanın etkin olduğu mevcut belgeleri ve çalışma kitaplarını kullanarak belge **düzeyinde projeler oluşturabilirsiniz.** Oturum açma Visual Studio Word ve Açık parola Excel belgeler **için davranış farklıdır.**

 Parolayı Açıkken etkinleştirme **hakkında bilgi için bkz.** Word veya Excel.

## <a name="behavior-of-excel-and-word"></a>Excel ve Word davranışı
 Açık Parola etkin Excel bir Visual Studio çalışma kitabını  her Excel sizden parola istenir. Çözüm ekleyebilirsiniz, çünkü belge derleme sırasında açıldığından parolayı yeniden girmeniz istenir.

 Açık'ta Parola etkin olan bir Visual Studio word  belgesini ilk kez a açmanız, Word sizden parolayı girmenizi sağlar. Parolayı başarıyla girdikten sonra **Açık** olan Parola belgeden kaldırılır ve belgeyi açmak için parolaya gerek yoktur. Çözüm belgenizin açılmadan önce parola gerektirmesini sağlamak için, son  derlemeden sonra ve çözümü dağıtmadan önce Aç'ta Parola'ya izin ve ardından parolayı etkinleştirmeniz gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Belge düzeyi çözümlerde belge koruması](../vsto/document-protection-in-document-level-solutions.md)
- [Bilgi hakları yönetimi ve yönetilen kod uzantılarına genel bakış](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Nasıl kullanılır: Kodun kısıtlı izinlerle belgelerin arkasında çalışmasına izin verme](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Yeni çözümler tasarlama Office oluşturma](../vsto/designing-and-creating-office-solutions.md)
