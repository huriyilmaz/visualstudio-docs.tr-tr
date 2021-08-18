---
title: IDE-Defined Komutları, Menüleri ve Grupları | Microsoft Docs
description: Tümleşik geliştirme ortamında (IDE) tanımlanan menüler, komutlar ve Visual Studio grupları hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 9f25616c97ed4f3b1e8402432a36db86e72edb58
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122042406"
---
# <a name="ide-defined-commands-menus-and-groups"></a>IDE Tanımlı Komutlar, Menüler ve Gruplar
Birçok menü, komut ve komut grubu IDE tarafından kullanmak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] üzere önceden tanımlanmıştır. Bu komutlar, genişletildikleri zaman da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kullanılabilir.

## <a name="finding-environment-defined-commands"></a>Komut Environment-Defined Bulma
 Ortam komutları dört .vsct dosyası kümesinde tanımlanır:

- SharedCmdDef.vsct

- SharedCmdPlace.vsct

- ShellCmdDef.vsct

- ShellCmdPlace.vsct

  Bu dosyalar *\<Visual Studio SDK installation path>* \VisualStudioIntegration\Common\Inc konumunda \\ bulunur. Bu dosyalar, VSPackage komut tablosu yapılandırması (.vsct) dosyasında kendi menüleriniz, gruplarınız ve komutlarınız için kapsayıcılar olarak kullanabileceğiniz menülerin ve grupların tanımlarını ve GUID'lerini sağlar.

## <a name="in-this-section"></a>Bu Bölümde
- [Visual Studio Menülerinin GUID’leri ve Kimlikleri](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

 Menü çubuğundaki menülerin GUID ve Visual Studio değerlerini ve içer çalıştıkları grupları verir.

- [Visual Studio Araç Çubuklarının GUID’leri ve Kimlikleri](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)

 IDE'de bulunan araç çubuklarının GUID ve Visual Studio değerlerini ve içer çalıştıkları grupları verir.

- [Visual Studio Komutlarının GUID’leri ve Kimlikleri](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)

 IDE tarafından tanımlanan komutların GUID ve kimlik Visual Studio verir.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Proje Sistemlerini Genişletmeye Yönelik IDE Tanımlı Komutlar](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
- [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
