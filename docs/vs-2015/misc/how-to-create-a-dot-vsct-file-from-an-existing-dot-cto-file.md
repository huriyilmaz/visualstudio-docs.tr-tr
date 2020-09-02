---
title: 'Nasıl yapılır: oluşturma. Varolan bir dosyadan vsct dosyası. CTO dosyası | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating based on a .cto file
ms.assetid: 847717c9-477d-4ac9-8b2c-2da878912478
caps.latest.revision: 11
manager: jillfra
ms.openlocfilehash: 83608d768940158dcdab427a557577677e56f7c8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62822444"
---
# <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Nasıl yapılır: oluşturma. Varolan bir dosyadan vsct dosyası. CTO dosyası
Var olan bir binary. CTO dosyasından XML tabanlı. vsct dosyası oluşturabilirsiniz. Bunun yapılması, yeni komut tablosu derleyici biçiminden yararlanmanızı sağlar. . Cto dosyası bir. CTC dosyasından derlense bile bu işlem işe yarar. . Vsct dosyasını başka bir. cto dosyasına düzenleyebilir ve derleyebilirsiniz.  
  
### <a name="to-create-a-vsct-file-from-a-cto-file"></a>. CTO dosyasından bir. vsct dosyası oluşturmak için  
  
1. . CTO dosyasının ve karşılık gelen. ctsyma dosyasının kopyalarını alın.  
  
2. Dosyaları vsct.exe derleyicisi ile aynı dizine yerleştirin.  
  
3. Visual Studio komut Isteminde. CTO ve. ctsyd dosyalarını içeren dizine gidin.  
  
4. **vsct.exe** _ctofilename_**. CTO** _vsctfilename_**. vsct-S**_symfilename_**. ctsyd**yazın.  
  
     `ctofilename` . CTO dosyasının adı, `vsctfilename` oluşturmak istediğiniz vsct dosyasının adıdır ve `symfilename` . ctsyd dosyasının adıdır.  
  
     Bu işlem yeni bir. vsct XML komut tablosu derleyici dosyası oluşturur. Dosyayı herhangi bir. vsct dosyası gibi vsct.exe, vsct derleyicisi ile düzenleyebilir ve derleyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: oluşturma. Vsct dosyası](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)