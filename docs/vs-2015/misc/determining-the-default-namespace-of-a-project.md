---
title: Projenin varsayılan ad alanını belirleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- custom tools, computing default namespace
ms.assetid: 6d890676-7016-458c-8a6a-95cc0a068612
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 1d58c8986922c30192d6300a623a635b24c34ed5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65705766"
---
# <a name="determining-the-default-namespace-of-a-project"></a>Projenin varsayılan ad alanını belirleme
İçin, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] `CustomToolNamespace` özelliği giriş dosyasında ayarlandıysa, değeri `CustomToolNamespace` yöntemine geçirilen varsayılan ad alanı parametresinin değeri olur <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> . Aksi takdirde, `wszDefaultNamespace` öğesine geçirilen parametresi `Generate` her zaman kök ad alanına eşittir. Ad alanları hakkında daha fazla bilgi için bkz. [ad alanı anahtar sözcükleri](https://msdn.microsoft.com/library/091a66eb-b10d-4f54-9102-5ac0d4bdb84b).  
  
 [!INCLUDE[csprcs](../includes/csprcs-md.md)] Klasör tabanlı ad alanlarını kullanır. Diğer bir deyişle, ad alanı kök ad alanından ve özel aracı içeren tüm klasörlerin adlarından oluşur. Her klasör adı geçerli bir tanımlayıcıya dönüştürülür ve dönemler tüm adları ayırır. Örneğin, giriş dosyası FolderA\FolderB\FolderC\MyInput.txt ve kök ad alanı CL9 ise, hesaplanan varsayılan ad alanı **CL9 olur. FolderA. FolderB. FolderC**.  
  
 Hiyerarşi zinciri bir Web başvurusu klasörü içerdiğinde, bu kural için bir özel durum oluşur. Örneğin:  
  
- FolderC bir Web başvuru klasörüdür, ad alanı **CL9 olacaktır. FolderC**.  
  
- FolderB bir Web başvuru klasörüdür, ad alanı **CL9 olacaktır. FolderB. FolderC**.  
  
  Diğer bir deyişle, ad alanı aşağıdaki biçimi kullanır:  
  
```  
rootNamespace.webReferenceFolder.containedFolder.containedFolder ...  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tek dosya oluşturucularını uygulama](../extensibility/internals/implementing-single-file-generators.md)   
 [Tek dosya oluşturucularını kaydetme](../extensibility/internals/registering-single-file-generators.md)   
 [Türleri Görsel Tasarımcıların Kullanımına Sunma](../extensibility/internals/exposing-types-to-visual-designers.md)