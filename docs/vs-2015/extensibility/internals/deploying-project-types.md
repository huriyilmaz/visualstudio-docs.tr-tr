---
title: Proje türlerini dağıtma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0fda84d5f7467a65b254d3b12b0466b6ab415d61
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196874"
---
# <a name="deploying-project-types"></a>Proje Türlerini Dağıtma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] Yeni bir proje türü toplayıcısı (ProjectAggregator2.dll) ve ayrıca yeniden dağıtım için bir Windows Installer paketi (ProjectAggregator2.msi) yüklenir. Yönetilen kod proje türleri için yeni toplayıcısı 'nı kullanmanız gerekir. ProjectAggregator2, proje toplayıcısı 'nda, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] yönetilen kod proje türlerinin düzgün çalışmasını engelleyen arounds sınırlamaları çalışır. Aşağıdaki adımlarda, VSPackage 'ın yeni toplayıcısı 'nı kullanacak şekilde nasıl değiştirileceği açıklanır.  
  
1. NativeHierarchyWrapper projesini çözümünüzden kaldırın.  
  
2. Tüm NativeHierarchyWrapper ikililerini kurulumınızdan kaldırın.  
  
3. ProjectAggregator2.msi, kuruluma ekleyin.
