---
title: Proje türlerini dağıtma | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 835e85ade4d309d0b5692aa9b857476cd6b5927a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708782"
---
# <a name="deploy-project-types"></a>Proje türlerini dağıt
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Yeni bir proje türü toplayıcısı (*ProjectAggregator2.dll*) ve ayrıca yeniden dağıtım için bir Windows Installer paketi (*ProjectAggregator2.msi*) yüklenir. Yönetilen kod proje türleri için yeni toplayıcısı 'nı kullanmanız gerekir. ProjectAggregator2, proje toplayıcısı 'nda, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yönetilen kod proje türlerinin düzgün çalışmasını engelleyen sınırlamalar çerçevesinde çalışır. Aşağıdaki adımlarda, VSPackage 'ın yeni toplayıcısı 'nı kullanacak şekilde nasıl değiştirileceği açıklanır.

1. NativeHierarchyWrapper projesini çözümünüzden kaldırın.

2. Tüm NativeHierarchyWrapper ikililerini kurulumınızdan kaldırın.

3. *ProjectAggregator2.msi* , kuruluma ekleyin.
