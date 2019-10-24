---
title: IDE tanımlı komutlar, menüler ve gruplar | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af6d3e180e2b3d5eb2e0f6c85b7488761e160c69
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727292"
---
# <a name="ide-defined-commands-menus-and-groups"></a>IDE Tanımlı Komutlar, Menüler ve Gruplar
Birçok menü, komut ve komut grubu, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE tarafından kullanılmak üzere zaten tanımlanmış. Bu komutlar, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]genişlettiğinizde kullanım için de kullanılabilir.

## <a name="finding-environment-defined-commands"></a>Ortam tanımlı komutları bulma
 Ortam komutları bir dizi dört. vsct dosyasında tanımlanır:

- SharedCmdDef. vsct

- SharedCmdPlace. vsct

- ShellCmdDef. vsct

- ShellCmdPlace. vsct

  Bu dosyalar *\<Visual STUDIO SDK yükleme yolunda >* \VisualStudioIntegration\Common\Inc\\bulunur. Bu dosyalar, VSPackage 'ın komut tablosu yapılandırma (. vsct) dosyasında kendi menü, Grup ve komutlarınız için kapsayıcı olarak kullanabileceğiniz menü ve grupların tanımlarını ve GUID 'Lerini sağlar.

## <a name="in-this-section"></a>Bu Bölümde
- [Visual Studio Menülerinin GUID’leri ve Kimlikleri](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

 Visual Studio menü çubuğunda ve içerdikleri gruplardan menülerin GUID ve ID değerlerini verir.

- [Visual Studio Araç Çubuklarının GUID’leri ve Kimlikleri](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)

 Visual Studio IDE 'deki araç çubuklarının GUID ve KIMLIK değerlerini ve içerdikleri grupları verir.

- [Visual Studio Komutlarının GUID’leri ve Kimlikleri](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)

 Visual Studio IDE tarafından tanımlanan komutların GUID ve ID değerlerini verir.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Proje Sistemlerini Genişletmeye Yönelik IDE Tanımlı Komutlar](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
- [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)