---
title: Düzenleyici ve dil hizmeti uzantıları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7fa3e4be6ee44011eb1286e3ebf22ee69f8e3397
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683111"
---
# <a name="editor-and-language-service-extensions"></a>Düzenleyici ve Dil Hizmeti Uzantıları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio Code Editor özelliklerinin çoğunu genişletebilirsiniz. Düzenleyici, Windows Presentation Foundation (WPF) temel alır ve yönetilen kodda yazılmıştır. Bu tasarım, Visual Studio 'nun önceki sürümlerindeki tasarımlardan farklı olsa da, aynı özelliklerin çoğunu sağlar. Düzenleyiciyi genişletmek için Managed Extensibility Framework (MEF) kullanın.  
  
 Visual Studio SDK, daha önceki sürümler için yazılmış VSPackages 'leri desteklemek üzere *dolgular* olarak bilinen bağdaştırıcılar sağlar. Bununla birlikte, mevcut bir VSPackage varsa, daha iyi performans ve güvenilirlik elde etmek için bunu yeni teknolojiyle güncelleştirmeniz önerilir.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Düzenleyici Öğesi Şablonuyla Uzantı Oluşturma](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Düzenleyici öğe şablonlarını kullanma konusuna giriş.|  
|[Düzenleyiciyi ve Dil Hizmetlerini Genişletme](../extensibility/extending-the-editor-and-language-services.md)|Temel düzenleyicinin tasarımını ve özelliklerini tanıtan ve onu genişletmeyi gösteren belgelerin bağlantıları.|  
|[Düzenleyicideki Eski Arabirimler](../extensibility/legacy-interfaces-in-the-editor.md)|Mevcut koddan çekirdek düzenleyiciye nasıl erişebileceğini açıklayan belgelerin bağlantıları.|  
|[Özel Düzenleyiciler ve Tasarımcılar Oluşturma](../extensibility/creating-custom-editors-and-designers.md)|Özel düzenleyiciler oluşturmayı açıklayan belgelerin bağlantıları.|  
|[Eski Dil Hizmeti Genişletilebilirliği](../extensibility/internals/legacy-language-service-extensibility.md)|Programlama dillerinin Visual Studio 'da nasıl tümleştirileceğini betimleyen belgelerin bağlantıları.|  
|[Managed Extensibility Framework (MEF)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Managed Extensibility Framework (MEF) tanıtır.|  
|[Windows Presentation Foundation](https://msdn.microsoft.com/library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Windows Presentation Foundation (WPF) tanıtır.|
