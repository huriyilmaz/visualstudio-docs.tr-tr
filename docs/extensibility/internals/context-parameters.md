---
title: Bağlam parametreleri | Microsoft Docs
description: Bir sihirbaz eklediğinizde veya uyguladığınızda projenin durumunu tanımlayan Visual Studio tümleşik geliştirme ortamında (IDE) bağlam parametreleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 72d2c6ded39564b91ba4f7b74fe2985aab14a7ce
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852641"
---
# <a name="context-parameters"></a>Bağlam parametreleri
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Tümleşik geliştirme ortamında (IDE), **yeni projeye** sihirbaz ekleyebilir, **Yeni öğe ekleyebilir** veya **alt proje** iletişim kutuları ekleyebilirsiniz. Eklenen sihirbazlar **Dosya** menüsünde veya **Çözüm Gezgini** bir projeye sağ tıklanarak kullanılabilir. IDE, sihirbazın uygulamasına bağlam parametrelerini geçirir. Bağlam parametreleri, IDE Sihirbazı çağırdığında projenin durumunu tanımlar.

 IDE, <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> IDE 'nin proje için metoduna olan bayrağını ayarlayarak sihirbazları başlatır <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> . Ayarlandığında, projenin, `IVsExtensibility::RunWizardFile` kayıtlı sihirbaz adı veya GUID 'si ve IDE 'nin kendisine geçirdiği diğer bağlam parametreleri kullanılarak, yöntemin yürütülmesine neden olması gerekir.

## <a name="context-parameters-for-new-project"></a>Yeni proje için bağlam parametreleri

| Parametre | Açıklama |
|-------------------------| - |
| `WizardType` | Kayıt Sihirbazı türü ( <xref:EnvDTE.Constants.vsWizardNewProject> ) veya sihirbazın türünü gösteren GUID. [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]Uygulamada, sihirbazın GUID 'si {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Benzersiz proje adı olan bir dize [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . |
| `LocalDirectory` | Çalışma projesi dosyalarının yerel konumu. |
| `InstallationDirectory` | Yüklemesinin dizin yolu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . |
| `FExclusive` | Projenin açık çözümleri kapatması gerektiğini belirten Boolean bayrağı. |
| `SolutionName` | Çözüm dosyasının dizin bölümü veya *. sln* uzantısı olmadan adı. *. Suo* dosya adı kullanılarak da oluşturulur `SolutionName` . Bu bağımsız değişken boş bir dize olmadığında, sihirbaz, <xref:EnvDTE._Solution.Create%2A> ile projeyi eklemeden önce kullanır <xref:EnvDTE._Solution.AddFromTemplate%2A> . Bu ad boş bir dize ise, öğesini <xref:EnvDTE._Solution.AddFromTemplate%2A> çağırmadan kullanın <xref:EnvDTE._Solution.Create%2A> . |
| `Silent` | **Son** tıklandığı gibi sihirbazın sessizce çalıştırılıp çalıştırılmayacağını belirten Boole değeri ( `TRUE` ). |

## <a name="context-parameters-for-add-new-item"></a>Yeni öğe Ekle için bağlam parametreleri

| Parametre | Açıklama |
|-------------------------| - |
| `WizardType` | Kayıt Sihirbazı türü ( <xref:EnvDTE.Constants.vsWizardAddItem> ) veya sihirbazın türünü gösteren GUID. [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]Uygulamada, sihirbazın GUID 'si {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Benzersiz proje adı olan bir dize [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . |
| `ProjectItems` | Çalışma projesi dosyalarını içeren yerel konum. |
| `ItemName` | Eklenecek öğenin adı. Bu ad, kullanıcının **öğe Ekle** iletişim kutusundan aldığı varsayılan dosya adı veya dosya adıdır. Ad, *. vsdir* dosyasında ayarlanan bayrakları temel alır. Ad, null bir değer olabilir. |
| `InstallationDirectory` | Yüklemesinin dizin yolu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . |
| `Silent` | **Son** tıklandığı gibi sihirbazın sessizce çalıştırılıp çalıştırılmayacağını belirten Boole değeri ( `TRUE` ). |

## <a name="context-parameters-for-add-sub-project"></a>Alt proje Ekle için bağlam parametreleri

| Parametre | Açıklama |
|-------------------------| - |
| `WizardType` | Kayıt Sihirbazı türü ( <xref:EnvDTE.Constants.vsWizardAddSubProject> ) veya sihirbazın türünü gösteren GUID. [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]Uygulamada, sihirbazın GUID 'si {0F90E1D2-4999-11D1-B6D1-00A0C90F2744} olur. |
| `ProjectName` | Benzersiz proje adı olan bir dize [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . |
| `ProjectItems` | `ProjectItems`Sihirbazın üzerinde çalıştığı koleksiyonun işaretçisi. Bu işaretçi, proje hiyerarşisi seçimine göre sihirbaza geçirilir. Kullanıcı genellikle öğenin ekleneceği bir klasörü seçer ve ardından projenin **öğe Ekle** iletişim kutusunu çağırır. |
| `LocalDirectory` | Çalışma projesi dosyalarının yerel konumu. |
| `ItemName` | Eklenecek öğenin adı. Bu ad, kullanıcının **öğe Ekle** iletişim kutusundan aldığı varsayılan dosya adı veya dosya adıdır. Ad, *. vsdir* dosyasında ayarlanan bayrakları temel alır. Ad, null bir değer olabilir. |
| `InstallationDirectory` | Yüklemenin dizin yolu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . |
| `Silent` | **Son** tıklandığı gibi sihirbazın sessizce çalıştırılıp çalıştırılmayacağını belirten Boole değeri ( `TRUE` ). |

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>
- [Özel parametreler](../../extensibility/internals/custom-parameters.md)
- [Sihirbazlar](../../extensibility/internals/wizards.md)
- [Sihirbaz (. vsz) dosyası](../../extensibility/internals/wizard-dot-vsz-file.md)
- [Sihirbazları başlatmak için bağlam parametreleri](/previous-versions/tz690efs(v=vs.140))