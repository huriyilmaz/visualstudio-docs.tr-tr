---
title: Bağlam Parametreleri | Microsoft Docs
description: Sihirbaz eklerken veya Visual Studio projenin durumunu tanımlayan tümleşik geliştirme ortamındaki (IDE) bağlam parametreleri hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 9b26006a7e178e5449825bb422be35ea2d83a392
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626187"
---
# <a name="context-parameters"></a>Bağlam parametreleri
Tümleşik [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] geliştirme ortamında (IDE) Yeni Uygulama, **Yeni Öğe Project** veya Alt Öğe Ekle iletişim kutularına **sihirbaz Project** ebilirsiniz. Eklenen sihirbazlar Dosya menüsünde veya **dosya** menüsündeki bir projeye sağ tık **Çözüm Gezgini.** IDE, bağlam parametrelerini sihirbazın uygulamasına iletir. Bağlam parametreleri, IDE sihirbazı çağıran projenin durumunu tanımlar.

 IDE, <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> IDE çağrısında bayrağını proje yöntemine ayarerek <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> sihirbazları başlatır. Bu ayar olduğunda, proje yöntemin kayıtlı sihirbaz adı veya GUID ve IDE'nin ona aktarmış olduğu diğer bağlam parametreleri kullanılarak `IVsExtensibility::RunWizardFile` yürütülür.

## <a name="context-parameters-for-new-project"></a>Yeni proje için bağlam parametreleri

| Parametre | Açıklama |
|-------------------------| - |
| `WizardType` | Kayıtlı sihirbaz türü <xref:EnvDTE.Constants.vsWizardNewProject> ( ) veya sihirbazın türünü belirten GUID. Uygulamada, sihirbazın GUID değeri [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] {0F90E1D0-4999-11D1-B6D1-00A0C90F2744} değeridir. |
| `ProjectName` | Benzersiz proje adı olan [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bir dize. |
| `LocalDirectory` | Çalışan proje dosyalarının yerel konumu. |
| `InstallationDirectory` | dizininin yolu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yüklemedir. |
| `FExclusive` | Projenin açık çözümleri kapatması gerektiğini belirten Boole bayrağı. |
| `SolutionName` | Dizin bölümü veya *.sln* uzantısı olmadan çözüm dosyasının adı. *.suo dosya* adı kullanılarak da `SolutionName` oluşturulur. Bu bağımsız değişken boş bir dize olduğunda, sihirbaz projeyi <xref:EnvDTE._Solution.Create%2A> ile eklemeden önce <xref:EnvDTE._Solution.AddFromTemplate%2A> kullanır. Bu ad boş bir dize ise, <xref:EnvDTE._Solution.AddFromTemplate%2A> çağırmadan <xref:EnvDTE._Solution.Create%2A> kullanın. |
| `Silent` | Sihirbazın Son'a tıklandı gibi sessizce  çalıştırıp çalıştırılamaycalığı belirten Boole ( `TRUE` ). |

## <a name="context-parameters-for-add-new-item"></a>Yeni Öğe Ekle bağlam parametreleri

| Parametre | Açıklama |
|-------------------------| - |
| `WizardType` | Kayıtlı sihirbaz türü <xref:EnvDTE.Constants.vsWizardAddItem> ( ) veya sihirbazın türünü belirten GUID. Uygulamada, sihirbazın GUID değeri [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}'tır. |
| `ProjectName` | Benzersiz proje adı olan [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bir dize. |
| `ProjectItems` | Çalışan proje dosyalarını içeren yerel konum. |
| `ItemName` | Eklenecek öğenin adı. Bu ad, kullanıcının Öğe Ekle iletişim kutusundan varsayılan dosya adı veya **dosya adıdır.** Ad, *.vsdir* dosyasında ayarlanmış bayrakları temel alan bir addır. Ad null değer olabilir. |
| `InstallationDirectory` | dizininin yolu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yüklemedir. |
| `Silent` | Sihirbazın Son'a tıklandı gibi sessizce  çalıştırıp çalıştırılamaycalığı belirten Boole ( `TRUE` ). |

## <a name="context-parameters-for-add-sub-project"></a>Alt Veri Ekle için bağlam Project

| Parametre | Açıklama |
|-------------------------| - |
| `WizardType` | Kayıtlı sihirbaz türü <xref:EnvDTE.Constants.vsWizardAddSubProject> ( ) veya sihirbazın türünü belirten GUID. Uygulamada, sihirbazın GUID değeri [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}'tır. |
| `ProjectName` | Benzersiz proje adı olan [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bir dize. |
| `ProjectItems` | Sihirbazın `ProjectItems` üzerinde çalıştır olduğu koleksiyonun işaretçisi. Bu işaretçi, proje hiyerarşisi seçimine göre sihirbaza geçirildi. Kullanıcı genellikle öğeyi koyarak projenin Öğe Ekle iletişim kutusunu çağıran bir **klasör** seçer. |
| `LocalDirectory` | Çalışan proje dosyalarının yerel konumu. |
| `ItemName` | Eklenecek öğenin adı. Bu ad, kullanıcının Öğe Ekle iletişim kutusundan varsayılan dosya adı veya **dosya adıdır.** Ad, *.vsdir* dosyasında ayarlanmış bayrakları temel alan bir addır. Ad null değer olabilir. |
| `InstallationDirectory` | Yüklemenin dizin [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yolu. |
| `Silent` | Sihirbazın Son'a tıklandı gibi sessizce  çalıştırıp çalıştırılamaycalığı belirten Boole ( `TRUE` ). |

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>
- [Özel parametreler](../../extensibility/internals/custom-parameters.md)
- [Sihirbazlar](../../extensibility/internals/wizards.md)
- [Sihirbaz (.vsz) dosyası](../../extensibility/internals/wizard-dot-vsz-file.md)
- [Sihirbazları başlatmak için bağlam parametreleri](/previous-versions/tz690efs(v=vs.140))