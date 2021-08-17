---
title: Visual Studio 2015 SDK'sı | Microsoft Docs
description: KAYNAK denetimi VSPackage'larının özellikleri hakkında bilgi edinin ve uygulama adımlarına genel bir bakış gözden geçirme.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 9f828aa153ddba9fcc0bb6db07084277b48b7c862447bd2b8fc4e6681123ab44
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121431740"
---
# <a name="whats-new-in-source-control-for-the-visual-studio-2015-sdk"></a>Visual Studio 2015 SDK'sı için Kaynak Denetiminde Neler Var

içinde, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] bir kaynak denetimi VSPackage'sı uygulayarak, derin bir tümleşik kaynak denetimi çözümü s hizmetleri s platformlarında kullanılabilirsiniz. Bu bölümde kaynak denetimi VSPackage'larının özellikleri açık ve uygulama adımlarına genel bir bakış sağlar.

## <a name="the-source-control-vspackage"></a>Kaynak Denetimi VSPackage

Visual Studio iki tür kaynak denetimi çözümü destekler. Uygulamanın tüm Visual Studio, Yine de Kaynak Denetimi Eklentisi API'si tabanlı eklentiyi tümleştirebilirsiniz. Ayrıca, yüksek düzeyde gelişmişlik ve otonomi gerektiren kaynak denetimi çözümleri için uygun bir derin tümleştirme ve yol sağlayan kaynak denetimi için bir VSPackage [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] da oluşturabilirsiniz.

VSPackage, uygulamanıza neredeyse her türlü işlevi Visual Studio. Kaynak denetimi VSPackage, kullanıcıya sunulan kullanıcı arabiriminden kaynak denetim sistemiyle arka uç iletişim Visual Studio için tam bir kaynak denetimi özelliği sağlar.

VSPackage kaynak denetimi uygulamak için "hepsi veya hiçbir şey" stratejisi gerekir. VSPackage kaynak denetimi oluşturucusu, kaynak denetimi işlevselliğinin tamamını kapsayacak şekilde bir dizi kaynak denetim arabirimi ve yeni kullanıcı arabirimi öğeleri (iletişim kutuları, menüler ve araç çubukları) uygulamak ve herhangi bir paketin Visual Studio ile başarıyla tümleştiril için gereken arabirimleri uygulamak için önemli miktarda çaba göster Visual Studio.

Aşağıdaki adımlar, bir kaynak denetim paketini uygulamak için gerekenlere genel bir genel bakış sağlar. Ayrıntılar için [bkz. Kaynak Denetimi VSPackage Oluşturma.](../../extensibility/internals/creating-a-source-control-vspackage.md)

1. Özel bir kaynak denetimi hizmetine sahip olan bir VSPackage oluşturun.

2. Kaynak denetimiyle ilgili hizmetlerde, arabirimler tarafından ara Visual Studio (örneğin, ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> arabirimi) uygulama.

3. VsPackage kaynak denetiminizi kaydetme.

4. Menü öğeleri, iletişim kutuları, araç çubukları ve bağlam menüleri dahil olmak üzere tüm kaynak denetimi kullanıcı arabirimini uygulama.

5. Kaynak denetimiyle ilgili tüm olaylar etkin olduğunda kaynak denetimi VSackage'nıza geçirildi ve VSPackage'nız tarafından işlerinin olması gerekir.

6. VsPackage kaynak denetiminiz, arabirimi uygulayan olaylar gibi olayları dinlemeli, Project Belgesi (TPD) olaylarını izlemeli (arabirim tarafından uygulanan şekilde) ve gerekli eylemi <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> gerçekleştirmalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Genel Bakış](../../extensibility/internals/source-control-integration-overview.md)
- [Kaynak Denetimi VSPackage’ı Oluşturma](../../extensibility/internals/creating-a-source-control-vspackage.md)
