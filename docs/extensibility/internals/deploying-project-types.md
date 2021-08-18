---
title: Dağıtım Project Türleri | Microsoft Docs
description: Visual Studio SDK'da yeni bir proje türü toplayıcısı ve yeniden dağıtım için Windows Yükleyicisi paketini kullanarak yönetilen kod proje türlerini Visual Studio öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 7b3cacbb9a816171209cc5f1cbdd87ed4a1d7a7b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086644"
---
# <a name="deploy-project-types"></a>Proje türlerini dağıtma
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]yeni bir proje türü toplayıcısı (*ProjectAggregator2.dll*) ve yeniden dağıtım için bir Windows Yükleyici *paketi*(ProjectAggregator2.msi). Yönetilen kod proje türleri için yeni toplayıcıyı kullan gerekir. ProjectAggregator2, yönetilen kodlu proje türlerinin düzgün bir şekilde çalışmasını engelleyen proje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] toplayıcısı sınırlamalarıyla çalışır. Aşağıdaki adımlarda, VSPackage'nızı yeni toplayıcıyı kullanmak üzere nasıl değiştiryebilirsiniz?

1. NativeHierarchyWrapper projesini çözümünüzden kaldırın.

2. Tüm NativeHierarchyWrapper ikili dosyalarını kurulumdan kaldırın.

3. Kurulum *ProjectAggregator2.msi* ekleme.
