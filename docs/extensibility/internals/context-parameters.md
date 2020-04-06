---
title: Bağlam Parametreleri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6673ad8f26c94165635b5f1bc652b91dcbbfd24f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709305"
---
# <a name="context-parameters"></a>Bağlam parametreleri
Tümleşik geliştirme ortamında (IDE), **Yeni Projeye**sihirbazlar ekleyebilir, **Yeni Öğe Ekle**veya Alt Proje iletişim kutuları **ekleyebilirsiniz.** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Eklenen sihirbazlar **Dosya** menüsünde veya **Solution Explorer'da**bir projeyi sağ tıklatarak kullanılabilir. IDE, bağlam parametrelerini sihirbazın uygulanmasına geçirir. Bağlam parametreleri, IDE sihirbazı aradığında projenin durumunu tanımlar.

 IDE, IDE'nin <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> çağrısındaki bayrağı proje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> yöntemine ayarlayarak sihirbazları başlatır. Ayarlandığında, proje kayıtlı `IVsExtensibility::RunWizardFile` sihirbaz adı veya GUID ve IDE'nin geçtiği diğer bağlam parametrelerini kullanarak yöntemin yürütülmesine neden olmalıdır.

## <a name="context-parameters-for-new-project"></a>Yeni proje için bağlam parametreleri

| Parametre | Açıklama |
|-------------------------| - |
| `WizardType` | Kayıtlı sihirbaz<xref:EnvDTE.Constants.vsWizardNewProject>türü ( ) veya sihirbaz türünü gösteren GUID. [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Uygulamada, sihirbaz için GUID {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Benzersiz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proje adı olan bir dize. |
| `LocalDirectory` | Çalışan proje dosyalarının yerel konumu. |
| `InstallationDirectory` | Dizin yolu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yüklemedir. |
| `FExclusive` | Projenin açık çözümleri kapatması gerektiğini belirten Boolean bayrağı. |
| `SolutionName` | Dizin bölümü veya *.sln* uzantısı olmayan çözüm dosyasının adı. *.suo* dosya adı da kullanılarak `SolutionName`oluşturulur. Bu bağımsız değişken boş bir dize <xref:EnvDTE._Solution.Create%2A> olmadığında, sihirbaz <xref:EnvDTE._Solution.AddFromTemplate%2A>projeyi . Bu ad boş bir dizeise, aramadan <xref:EnvDTE._Solution.AddFromTemplate%2A> <xref:EnvDTE._Solution.Create%2A>kullanın. |
| `Silent` | Sihirbazın **Bitiş** tıklanmış gibi sessizce çalışması gerekip`TRUE`gerekmediğini belirten boolean ( ). |

## <a name="context-parameters-for-add-new-item"></a>Yeni Öğe Ekle için bağlam parametreleri

| Parametre | Açıklama |
|-------------------------| - |
| `WizardType` | Kayıtlı sihirbaz<xref:EnvDTE.Constants.vsWizardAddItem>türü ( ) veya sihirbaz türünü gösteren GUID. [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Uygulamada, sihirbaz için GUID {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Benzersiz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proje adı olan bir dize. |
| `ProjectItems` | Çalışan proje dosyalarını içeren yerel konum. |
| `ItemName` | Eklenecek öğenin adı. Bu ad, varsayılan dosya adı veya kullanıcının Öğeleri **Ekle** iletişim kutusundan yazdığı dosya adıdır. Ad, *.vsdir* dosyasında ayarlanan bayraklara dayanır. Ad null değeri olabilir. |
| `InstallationDirectory` | Dizin yolu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yüklemedir. |
| `Silent` | Sihirbazın **Bitiş** tıklanmış gibi sessizce çalışması gerekip`TRUE`gerekmediğini belirten boolean ( ). |

## <a name="context-parameters-for-add-sub-project"></a>Alt Proje Ekle için bağlam parametreleri

| Parametre | Açıklama |
|-------------------------| - |
| `WizardType` | Kayıtlı sihirbaz<xref:EnvDTE.Constants.vsWizardAddSubProject>türü ( ) veya sihirbaz türünü gösteren GUID. [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Uygulamada, sihirbaz için GUID {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Benzersiz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proje adı olan bir dize. |
| `ProjectItems` | Sihirbazın `ProjectItems` çalıştığı koleksiyona işaretçi. Bu işaretçi, proje hiyerarşisi seçimine göre sihirbaza geçirilir. Kullanıcı genellikle öğeyi koymak için bir klasör seçer ve sonra projenin **Öğe Ekle** iletişim kutusunu çağırır. |
| `LocalDirectory` | Çalışan proje dosyalarının yerel konumu. |
| `ItemName` | Eklenecek öğenin adı. Bu ad, varsayılan dosya adı veya kullanıcının Öğeleri **Ekle** iletişim kutusundan yazdığı dosya adıdır. Ad, *.vsdir* dosyasında ayarlanan bayraklara dayanır. Ad null değeri olabilir. |
| `InstallationDirectory` | Yüklemenin dizin [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] yolu. |
| `Silent` | Sihirbazın **Bitiş** tıklanmış gibi sessizce çalışması gerekip`TRUE`gerekmediğini belirten boolean ( ). |

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>
- [Özel parametreler](../../extensibility/internals/custom-parameters.md)
- [Sihirbazlar](../../extensibility/internals/wizards.md)
- [Sihirbaz (.vsz) dosyası](../../extensibility/internals/wizard-dot-vsz-file.md)
- [Başlatma sihirbazları için bağlam parametreleri](https://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)
