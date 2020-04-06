---
title: Visual Studio 2015 SDK'da Kaynak Kontrolünde Yenilikler | Microsoft Dokümanlar
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f90ae3e1d327b10e99713ad28aa2d5a06c0be34b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703404"
---
# <a name="whats-new-in-source-control-for-the-visual-studio-2015-sdk"></a>Visual Studio 2015 SDK Için Kaynak Kontrolünde Yenilikler

[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]Bir kaynak denetimi VSPackage uygulayarak derinentegre bir kaynak kontrol çözümü sağlayabilir. Bu bölümde kaynak denetimi VSPackages özellikleri açıklanır ve uygulama adımları genel bir bakış sağlar.

## <a name="the-source-control-vspackage"></a>Kaynak Kontrol VSPackage

Visual Studio iki tür kaynak kontrol çözümlerini destekler. Visual Studio'nun tüm sürümlerinde, kaynak denetimi eklentisi API tabanlı eklentiyi yine de entegre edebilirsiniz. Ayrıca, yüksek düzeyde gelişmişlik ve özerklik gerektiren kaynak [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] denetim çözümleri için uygun derin bir entegrasyon, yol sağlayan kaynak denetimi için bir VSPackage oluşturabilirsiniz.

Bir VSPackage Visual Studio işlevsellik hemen hemen her türlü ekleyebilirsiniz. Bir kaynak denetimi VSPackage Visual Studio için tam bir kaynak kontrol özelliği sağlar, Kullanıcıya sunulan ui kaynak kontrol sistemi ile arka uç iletişim için.

Bir kaynak denetimi VSPackage uygulanması bir "ya hep ya hiç" stratejisi gerektirir. Bir kaynak denetimi VSPackage yaratıcısı kaynak denetim arabirimleri ve yeni UI öğeleri (iletişim kutuları, menüler ve araç çubukları) tüm kaynak kontrol işlevselliğini kapsayacak şekilde bir dizi uygulanması çaba önemli miktarda yatırım gerekir, yanı sıra herhangi bir paket için gerekli arayüzler Visual Studio ile başarılı bir şekilde entegre etmek için gerekli.

Aşağıdaki adımlar, bir kaynak denetim paketi uygulamak için gerekenlerhakkında genel bir genel bakış sağlar. Ayrıntılar için [kaynak denetimi VSPackage oluşturma](../../extensibility/internals/creating-a-source-control-vspackage.md)konusuna bakın.

1. Özel kaynak kontrol hizmeti sunan bir VSPackage oluşturun.

2. Visual Studio tarafından sunulan kaynak denetimi ile ilgili hizmetlerdeki arabirimleri uygulayın (örneğin, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> arabirim).

3. Kaynak denetiminizi VSPackage olarak kaydedin.

4. Menü öğeleri, iletişim kutuları, araç çubukları ve bağlam menüleri dahil olmak üzere tüm kaynak denetimi ui'lerini uygulayın.

5. Kaynak denetimiyle ilgili tüm olaylar, etkin olduğunda kaynak denetimivsackage'ınıza aktarılır ve VSPackage'ınız tarafından ele alınması gerekir.

6. Kaynak denetiminiz VSPackage, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> arabirimi uygulayanlar ve Proje Belgesi (TPD) olaylarını takip etme <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> (arayüz tarafından uygulandığı gibi) gibi olayları dinlemeli ve gerekli eylemi gerçekleştirmelidir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Genel bakış](../../extensibility/internals/source-control-integration-overview.md)
- [Kaynak Denetimi VSPackage’ı Oluşturma](../../extensibility/internals/creating-a-source-control-vspackage.md)
