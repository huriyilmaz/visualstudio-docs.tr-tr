---
title: Iç Içe projeler için sihirbaz desteği | Microsoft Docs
description: Bir üst projenin, Visual Studio SDK 'sında VSPackage 'inizdeki iç içe projeler için uygulayamayacağı iki sihirbaz hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f2cd84379ead1cd45296ae370aab215a37cf4b50
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935899"
---
# <a name="wizard-support-for-nested-projects"></a>İç içe Projeler için Sihirbaz Desteği
IDE, iç içe projeler için üst projenin uygulayamayacağı iki sihirbaz çalıştırır: **Yeni proje** Sihirbazı ve **öğe ekleme** Sihirbazı.

 Kullanıcı **Yeni** proje sihirbazını, Dosya menüsünde **Proje Ekle** ve **yeni** proje öğesine tıklayarak veya Çözüm Gezgini ' de **Yeni proje** **Ekle** ve sağ tıklama ' yi seçerek çalıştırıyorsa, IDE **AddProject** komutunu çalıştırır ve üst projenin **AddProject** komutunun uygulanması, bir şablon proje dosyası ya da bir bağlam parametreleri kümesine sahip bir sihirbaz (. vsz) dosyası döndürür.

 Benzer şekilde, bir üst projenin **AddItem** sihirbazları 'nın uygulanması, farklı bağlam parametreleri kümesine sahip bir. vsz dosyası döndürür.

 Sihirbazlar hakkında daha fazla bilgi için bkz [. sihirbaz (. Vsz) dosyası](../../extensibility/internals/wizard-dot-vsz-file.md), [Bağlam parametreleri](../../extensibility/internals/context-parameters.md) ve [Proje ve öğe şablonlarını kaydetme](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Projeleri İç İçe Geçirme](../../extensibility/internals/nesting-projects.md)
