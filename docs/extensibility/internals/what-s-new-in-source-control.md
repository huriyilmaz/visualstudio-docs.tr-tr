---
title: Visual Studio 2015 SDK 'da kaynak denetimindeki yenilikler | Microsoft Docs
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
ms.workload:
- vssdk
ms.openlocfilehash: da10750629fcdae66ab8456b3074c07f44e3cf05
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069068"
---
# <a name="whats-new-in-source-control-for-the-visual-studio-2015-sdk"></a>Visual Studio 2015 SDK için kaynak denetimindeki yenilikler

İçinde [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , bir kaynak denetimi VSPackage uygulayarak bir çok Tümleşik kaynak denetimi çözümü sağlayabilirsiniz. Bu bölümde, VSPackages kaynak denetimi özellikleri açıklanmakta ve uygulama adımlarına genel bir bakış sağlanmaktadır.

## <a name="the-source-control-vspackage"></a>Kaynak denetimi VSPackage

Visual Studio iki tür kaynak denetimi çözümünü destekler. Visual Studio 'nun tüm sürümlerinde, yine de bir kaynak denetimi eklentisi API tabanlı eklentisini tümleştirmenize devam edebilirsiniz. Ayrıca, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] yüksek düzeyde gelişmiş algoritmaların mümkündür ve bağımsız çalışma sınırı gerektiren kaynak denetimi çözümlerine uygun bir derin tümleştirme sağlayan kaynak denetimi için bir VSPackage oluşturabilirsiniz.

VSPackage, Visual Studio 'ya neredeyse her türlü işlevselliği ekleyebilir. Kaynak denetimi VSPackage, kullanıcıya kaynak denetim sistemi ile arka uç iletişimine sunulan Kullanıcı ARABIRIMINDEN, Visual Studio için tam bir kaynak denetimi özelliği sağlar.

Kaynak denetimi VSPackage uygulamak, "tümü veya Nothing" stratejisi gerektirir. Bir kaynak denetimi, VSPackage oluşturucusunun, kaynak denetimi işlevselliğinin tamamını kapsayan bir dizi kaynak denetim arabirimini ve yeni kullanıcı arabirimi öğelerini (iletişim kutuları, menüler ve araç çubukları) uygulamak için önemli miktarda çaba yatırması gerekir. böylece, Visual Studio ile başarılı bir şekilde tümleştirilebilir.

Aşağıdaki adımlarda, kaynak denetimi paketinin uygulanması için gerekli olan genel bir genel bakış sunulmaktadır. Ayrıntılar için bkz. [kaynak denetimi VSPackage oluşturma](../../extensibility/internals/creating-a-source-control-vspackage.md).

1. Özel bir kaynak denetimi hizmetini hedefleyen bir VSPackage oluşturun.

2. Arabirimleri, Visual Studio tarafından (örneğin, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> ve arabirimi) yapılan kaynak denetimi ile ilgili hizmetlerde uygulayın <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> .

3. Kaynak denetimi VSPackage 'a kaydolun.

4. Menü öğeleri, iletişim kutuları, araç çubukları ve bağlam menüleri dahil olmak üzere tüm kaynak denetimi kullanıcı arabirimini uygulayın.

5. Kaynak denetimi ile ilgili tüm olaylar etkinken kaynak denetimine geçirilir ve VSPackage tarafından işlenmesi gerekir.

6. Kaynak denetimi VSPackage, arabirimi uygulayan gibi olayları dinlemesi <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> ve proje belgesi (TPD) olaylarını (arabirim tarafından uygulandığı şekilde <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> ) izleyip gerekli işlemleri gerçekleştirmelidir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Genel Bakış](../../extensibility/internals/source-control-integration-overview.md)
- [Kaynak Denetimi VSPackage’ı Oluşturma](../../extensibility/internals/creating-a-source-control-vspackage.md)
