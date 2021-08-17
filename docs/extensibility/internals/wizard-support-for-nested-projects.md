---
title: Iç Içe projeler için sihirbaz desteği | Microsoft Docs
description: bir üst projenin, Visual Studio SDK 'sında vspackage 'inizdeki iç içe projeler için uygulayamayacağı iki sihirbaz hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c0fdc97b8ef15b4fdfd8fee13affb52b1935b80f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122041717"
---
# <a name="wizard-support-for-nested-projects"></a>İç içe Projeler için Sihirbaz Desteği
ıde, iç içe projeler için üst projenin uygulayamayacağı iki sihirbaz çalıştırır: **yeni Project** sihirbazı ve **öğe ekleme** sihirbazı.

 kullanıcı ekle ' yi seçerek veya dosya menüsünde **yeni Project** ' ye tıklayarak ya da **ekle** ve **Project** sağ Çözüm Gezgini ' yi seçerek **Project** yeni **Project** sihirbazı 'nı çalıştırıyorsa, ıde **addproject** komutunu çalıştırır ve üst projenin **addproject** komutunun uygulanması, bir şablon proje dosyası ya da bir bağlam parametreleri kümesine sahip bir sihirbaz (. vsz) dosyası döndürür.

 Benzer şekilde, bir üst projenin **AddItem** sihirbazları 'nın uygulanması, farklı bağlam parametreleri kümesine sahip bir. vsz dosyası döndürür.

 Sihirbazlar hakkında daha fazla bilgi için bkz [. sihirbaz (. Vsz) dosyası](../../extensibility/internals/wizard-dot-vsz-file.md), [bağlam parametreleri](../../extensibility/internals/context-parameters.md) ve [kayıt Project ve öğe şablonları](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Projeleri İç İçe Geçirme](../../extensibility/internals/nesting-projects.md)
