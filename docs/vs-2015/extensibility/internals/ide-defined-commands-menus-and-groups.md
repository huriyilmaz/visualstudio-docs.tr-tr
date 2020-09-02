---
title: IDE tanımlı komutlar, menüler ve gruplar | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 32e8135328c11fd74311371d07645a525426371e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192732"
---
# <a name="ide-defined-commands-menus-and-groups"></a>IDE Tanımlı Komutlar, Menüler ve Gruplar
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Birçok menü, komut ve komut grubu, IDE tarafından kullanılmak üzere zaten tanımlanmış [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Bu komutlar, uzatdığınızda kullanım için de kullanılabilir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="finding-environment-defined-commands"></a>Ortam tanımlı komutları bulma  
 Ortam komutları bir dizi dört. vsct dosyasında tanımlanır:  
  
- SharedCmdDef. vsct  
  
- SharedCmdPlace. vsct  
  
- ShellCmdDef. vsct  
  
- ShellCmdPlace. vsct  
  
  Bu dosyalar \VisualStudioIntegration\Common\Inc konumunda bulunur *\<Visual Studio SDK installation path>* \\ . Bu dosyalar, VSPackage 'ın komut tablosu yapılandırma (. vsct) dosyasında kendi menü, Grup ve komutlarınız için kapsayıcı olarak kullanabileceğiniz menü ve grupların tanımlarını ve GUID 'Lerini sağlar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Visual Studio Menülerinin GUID’leri ve Kimlikleri](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)  
 Visual Studio menü çubuğunda ve içerdikleri gruplardan menülerin GUID ve ID değerlerini verir.  
  
 [Visual Studio Araç Çubuklarının GUID’leri ve Kimlikleri](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)  
 Visual Studio IDE 'deki araç çubuklarının GUID ve KIMLIK değerlerini ve içerdikleri grupları verir.  
  
 [Visual Studio Komutlarının GUID’leri ve Kimlikleri](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)  
 Visual Studio IDE tarafından tanımlanan komutların GUID ve ID değerlerini verir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio komut tablosu (. Vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Proje sistemlerini genişletmek için IDE tanımlı komutlar](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)   
 [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
