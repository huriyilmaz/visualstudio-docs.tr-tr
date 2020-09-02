---
title: Iç Içe projeler için sihirbaz desteği | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 206fd12ea8f198e1659a49ed566e726e49878c53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180334"
---
# <a name="wizard-support-for-nested-projects"></a>İç içe Projeler için Sihirbaz Desteği
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

IDE, iç içe projeler için üst projenin uygulayamayacağı iki sihirbaz çalıştırır: **Yeni proje** Sihirbazı ve **öğe ekleme** Sihirbazı.  
  
 Kullanıcı **Yeni** proje sihirbazını, Dosya menüsünde **Proje Ekle** ve **yeni** proje öğesine tıklayarak veya Çözüm Gezgini ' de **Yeni proje** **Ekle** ve sağ tıklama ' yi seçerek çalıştırıyorsa, IDE **AddProject** komutunu çalıştırır ve üst projenin **AddProject** komutunun uygulanması, bir şablon proje dosyası ya da bir bağlam parametreleri kümesine sahip bir sihirbaz (. vsz) dosyası döndürür.  
  
 Benzer şekilde, bir üst projenin **AddItem** sihirbazları 'nın uygulanması, farklı bağlam parametreleri kümesine sahip bir. vsz dosyası döndürür.  
  
 Sihirbazlar hakkında daha fazla bilgi için bkz [. sihirbaz (. Vsz) dosyası](../../extensibility/internals/wizard-dot-vsz-file.md), [Bağlam parametreleri](../../extensibility/internals/context-parameters.md) ve [Proje ve öğe şablonlarını kaydetme](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Projeleri İç İçe Geçirme](../../extensibility/internals/nesting-projects.md)
