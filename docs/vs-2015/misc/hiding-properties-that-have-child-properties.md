---
title: Alt özellikleri olan özellikleri gizleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], hiding
- Properties window, hiding properties that have child properties
ms.assetid: 6003607e-fc19-4bf9-a299-9f6adf8e92eb
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 1d20b865c6f07d76320a7df8402810c82869ddfb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62822392"
---
# <a name="hiding-properties-that-have-child-properties"></a>Alt özellikleri olan özellikleri gizleme
Alt özellikleri olan özellikleri gizlemek isteyebilirsiniz:  
  
- Üst projenin program aracılığıyla alt projenin bazı yönlerini denetlediği iç içe projeler varsa.  
  
- Özelleştirilmiş tasarımcı ile bir denetim kullanıyorsanız ve geliştiricilere, denetimin tüm özelliklerine tam erişim vermek istemiyorsanız.  
  
- Bir nesnenin kapsam sahipliğiniz varsa ve özelliklerin görünümünü sınırlamak istiyorsanız.  
  
### <a name="to-hide-properties-that-have-child-properties"></a>Alt özellikleri olan özellikleri gizlemek için  
  
1. `pfDisplay`Parametresini <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> olarak ayarlayın `FALSE` .  
  
2. `pfHide`Parametresini <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> olarak ayarlayın `TRUE` .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özellikler Görüntü Kılavuzu](../extensibility/internals/properties-display-grid.md)