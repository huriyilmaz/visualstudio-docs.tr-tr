---
title: Visual Studio 2015 SDK 'sindeki kaynak denetimindeki yenilikler | Microsoft Docs
description: Kaynak denetimi VSPackages özellikleri hakkında bilgi edinin ve uygulama adımlarına genel bir bakış inceleyin.
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
ms.openlocfilehash: 2a2d24999f181edbbff3ed1a7a77eeaf5e0ff9cc
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726920"
---
# <a name="whats-new-in-source-control-for-the-visual-studio-2015-sdk"></a>Visual Studio 2015 SDK 'sı için kaynak denetimindeki yenilikler

İçinde [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , bir kaynak denetimi VSPackage uygulayarak bir çok Tümleşik kaynak denetimi çözümü sağlayabilirsiniz. Bu bölümde, VSPackages kaynak denetimi özellikleri açıklanmakta ve uygulama adımlarına genel bir bakış sağlanmaktadır.

## <a name="the-source-control-vspackage"></a>Kaynak denetimi VSPackage

Visual Studio iki tür kaynak denetimi çözümünü destekler. tüm Visual Studio sürümlerinde, yine de bir kaynak denetimi eklentisi apı tabanlı eklentisini tümleştirmenize devam edebilirsiniz. Ayrıca, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] yüksek düzeyde gelişmiş algoritmaların mümkündür ve bağımsız çalışma sınırı gerektiren kaynak denetimi çözümlerine uygun bir derin tümleştirme sağlayan kaynak denetimi için bir VSPackage oluşturabilirsiniz.

VSPackage, Visual Studio için neredeyse her türlü işlevi ekleyebilir. kaynak denetimi vspackage, kullanıcıya sunulan kullanıcı arabiriminden, kaynak denetim sistemi ile arka uç iletişimine kadar Visual Studio için tam bir kaynak denetimi özelliği sağlar.

Kaynak denetimi VSPackage uygulamak, "tümü veya Nothing" stratejisi gerektirir. Kaynak denetimini oluşturan VSPackage, kaynak denetimi işlevselliğinin tamamını kapsayan çok sayıda kaynak denetimi arabirimi ve yeni UI öğeleri (iletişim kutuları, menüler ve araç çubukları) uygulamak için önemli miktarda çaba yatırmalıdır. Ayrıca, Visual Studio ile başarıyla tümleştirilecek her pakette gerekli arabirimler vardır.

Aşağıdaki adımlarda, kaynak denetimi paketinin uygulanması için gerekli olan genel bir genel bakış sunulmaktadır. Ayrıntılar için bkz. [kaynak denetimi VSPackage oluşturma](../../extensibility/internals/creating-a-source-control-vspackage.md).

1. Özel bir kaynak denetimi hizmetini hedefleyen bir VSPackage oluşturun.

2. Visual Studio (örneğin, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> ve arabirimi) tarafından kullanılabilen kaynak denetimi ile ilgili hizmetlerde arabirimler uygulayın <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> .

3. Kaynak denetimi VSPackage 'a kaydolun.

4. Menü öğeleri, iletişim kutuları, araç çubukları ve bağlam menüleri dahil olmak üzere tüm kaynak denetimi kullanıcı arabirimini uygulayın.

5. Kaynak denetimi ile ilgili tüm olaylar etkinken kaynak denetimine geçirilir ve VSPackage tarafından işlenmesi gerekir.

6. kaynak denetimi vspackage, arabirimi uygulayan gibi olayları dinlemesi <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> ve Project Document (TPD) olaylarını izleyip <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> gerekli işlemleri gerçekleştirmelidir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Genel Bakış](../../extensibility/internals/source-control-integration-overview.md)
- [Kaynak Denetimi VSPackage’ı Oluşturma](../../extensibility/internals/creating-a-source-control-vspackage.md)
