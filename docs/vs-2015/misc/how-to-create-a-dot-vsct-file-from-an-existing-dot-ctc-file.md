---
title: 'Nasıl yapılır: oluşturma. Varolan bir dosyadan vsct dosyası. CTC dosyası | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating based on a .ctc file
ms.assetid: 700e80a4-c1e1-4178-af53-45e86dd2c08b
caps.latest.revision: 9
manager: jillfra
ms.openlocfilehash: 7b963436e9d968dd5ba3829e97d0fd0c52e49641
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64796915"
---
# <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Nasıl yapılır: oluşturma. Varolan bir dosyadan vsct dosyası. CTC dosyası
Varolan bir komut tablosu. ctc kaynak dosyasından XML tabanlı. vsct dosyası oluşturabilirsiniz. Bunu yaparak, yeni XML tabanlı [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] komut tablosu (VSCT) derleyici biçiminden yararlanabilirsiniz.  
  
### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>. CTC dosyasından bir. vsct dosyası oluşturmak için  
  
1. Perl dilinin bir kopyasını alın.  
  
2. Genellikle \VisualStudioIntegration\Tools\bin klasöründe bulunan Perl betiğinin ConvertCTCToVSCT.pl bir kopyasını alın *\<Visual Studio SDK installation path>* .  
  
3. Dönüştürmek istediğiniz. ctc kaynak dosyasının bir kopyasını alın.  
  
4. Dosyaları aynı dizine yerleştirin.  
  
5. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Komut istemi penceresinde, dizinine gidin.  
  
6. Tür  
  
    ```  
    perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
    ```  
  
     Burada PkgCmd. CTC,. CTC dosyasının adı ve PkgCmd. vsct, oluşturmak istediğiniz. vsct dosyasının adıdır.  
  
     Bu, yeni bir. vsct XML komut tablosu kaynak dosyası oluşturur. Dosyayı, başka bir. vsct dosyası gibi Vsct.exe, VSCT derleyicisini kullanarak derleyebilirsiniz.  
  
    > [!NOTE]
    > XML açıklamalarını yeniden düzenleyerek. vsct dosyasının okunabilirliğini geliştirebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: oluşturma. Vsct dosyası](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)