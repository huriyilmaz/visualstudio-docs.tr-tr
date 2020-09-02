---
title: 'Nasıl yapılır: VSıX paketine bağımlılık ekleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 997c0df133b72d69dfb4e69de53a1b77e1a0965c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697503"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Nasıl Yapılır: VSIX Paketine Bağımlılık Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hedef bilgisayarda zaten mevcut olmayan bağımlılıkları yükleyen bir VSıX paketi dağıtımı ayarlayabilirsiniz. Bunu gerçekleştirmek için, kaynak. Extension. valtmanifest dosyasına VSıX bağımlılıklarını ekleyin.  
  
#### <a name="to-add-a-dependency"></a>Bir bağımlılık eklemek için  
  
1. **Design** görünümünde Source. Extension. valtmanifest dosyasını açın. **Bağımlılıklar** sekmesine gidin ve **Yeni**' ye tıklayın.  
  
2. Yüklü bir uzantı eklemek için: **Yeni bağımlılık Ekle** iletişim kutusunda, **yüklü uzantı** ' ı seçin ve ardından **ad**için listeden bir uzantı seçin.  
  
3. Yüklü olmayan başka bir VSıX eklemek için:: **Yeni bağımlılık Ekle** iletişim kutusunda **dosya sistemindeki dosya** ' yı seçin ve ardından VSIX ' i seçmek için **Araştır** düğmesini kullanın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSıX uzantı şeması 1,0 başvurusu](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [VSıX paketinin anatomumu](../extensibility/anatomy-of-a-vsix-package.md)   
 [Uzantıları Windows Installer Dağıtımı için Hazırlama](../extensibility/preparing-extensions-for-windows-installer-deployment.md)
