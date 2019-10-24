---
title: Iç Içe projeler için sihirbaz desteği | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e498f21499f4b07bf77bb79829fc6d92227f1f2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721429"
---
# <a name="wizard-support-for-nested-projects"></a>İç içe Projeler için Sihirbaz Desteği
IDE, iç içe projeler için üst projenin uygulayamayacağı iki sihirbaz çalıştırır: **Yeni proje** Sihirbazı ve **öğe ekleme** Sihirbazı.

 Bir Kullanıcı **Yeni proje** sihirbazını, Dosya menüsünde **Proje Ekle** ve **Yeni proje** ' ye tıklayarak ya da **Ekle** ' yi seçip çözüm GEZGINI **Yeni proje** ' yi seçerek başlarsa, IDE **AddProject 'i çalıştırır** komut ve üst projenin **AddProject** komutunun uygulanması, bir şablon proje dosyası ya da bağlam parametreleri kümesine sahip bir sihirbaz (. vsz) dosyası döndürür.

 Benzer şekilde, bir üst projenin **AddItem** sihirbazları 'nın uygulanması, farklı bağlam parametreleri kümesine sahip bir. vsz dosyası döndürür.

 Sihirbazlar hakkında daha fazla bilgi için bkz [. sihirbaz (. Vsz) dosyası](../../extensibility/internals/wizard-dot-vsz-file.md), [Bağlam parametreleri](../../extensibility/internals/context-parameters.md) ve [Proje ve öğe şablonlarını kaydetme](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Projeleri İç İçe Geçirme](../../extensibility/internals/nesting-projects.md)