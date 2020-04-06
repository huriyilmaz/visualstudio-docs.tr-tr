---
title: IDE Tanımlı Komutlar, Menüler ve Gruplar | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6557f49b019a6793698dabe852919ec2e9f28cfd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707726"
---
# <a name="ide-defined-commands-menus-and-groups"></a>IDE Tanımlı Komutlar, Menüler ve Gruplar
Birçok menü, komut ve komut grubu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Zaten IDE tarafından kullanılmak üzere tanımlanmıştır. Bu komutları uzattığınızda [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]da kullanımınız için kullanılabilir.

## <a name="finding-environment-defined-commands"></a>Çevre Tanımlı Komutları Bulma
 Ortam komutları dört .vsct dosyası kümesinde tanımlanır:

- PaylaşılanCmdDef.vsct

- PaylaşılanCmdPlace.vsct

- ShellCmdDef.vsct

- ShellCmdPlace.vsct

  Bu dosyalar * \<Visual Studio SDK yükleme yolu>* \VisualStudioIntegration\Common\Inc\\bulunur. Bu dosyalar, VSPackage'ınızın komut tablosu yapılandırmasında (.vsct) kendi menüleriniz, gruplarınız ve komutlarınız için kapsayıcı olarak kullanabileceğiniz menülerin ve grupların tanımlarını ve GUID'lerini sağlar.

## <a name="in-this-section"></a>Bu Bölümde
- [Visual Studio Menülerinin GUID’leri ve Kimlikleri](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

 Visual Studio menü çubuğundaki menülerin ve içerdikleri grupların GUID ve kimlik değerlerini verir.

- [Visual Studio Araç Çubuklarının GUID’leri ve Kimlikleri](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)

 Visual Studio IDE'deki araç çubuklarının ve içerdikleri grupların GUID ve kimlik değerlerini verir.

- [Visual Studio Komutlarının GUID’leri ve Kimlikleri](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)

 Visual Studio IDE tarafından tanımlanan komutların GUID ve kimlik değerlerini verir.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Proje Sistemlerini Genişletmeye Yönelik IDE Tanımlı Komutlar](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
- [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
