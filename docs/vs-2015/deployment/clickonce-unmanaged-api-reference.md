---
title: ClickOnce yönetilmeyen API başvurusu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- LaunchApplication [ClickOnce unmanaged]
- ClickOnce, unmanaged APIs
- CleanOnlineAppCache [ClickOnce unmanaged]
- CleanOnlineAppCacheW interface [ClickOnce unmanaged]
- GetDeploymentDataFromManifest [ClickOnce unmanaged]
ms.assetid: ec002138-4054-456d-bcc1-79ac2f4a4fd7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 714d7b18995bf1ad51b07e02227e440879f73c9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192313"
---
# <a name="clickonce-unmanaged-api-reference"></a>ClickOnce Yönetilmeyen API Başvurusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dfshim.dll 'ten yönetilmeyen ortak API 'Ler.  
  
## <a name="cleanonlineappcache"></a>CleanOnlineAppCache  
 Tüm çevrimiçi uygulamaları uygulama önbelleğinden temizler veya kaldırır [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] .  
  
### <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa S_OK döndürür; Aksi takdirde, hatayı temsil eden bir HRESULT döndürür. Yönetilen bir özel durum oluşursa, 0x80020009 (DISP_E_EXCEPTION) döndürür.  
  
### <a name="remarks"></a>Açıklamalar  
 CleanOnlineAppCache çağrısı, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] zaten çalışmıyorsa hizmeti başlatacak.  
  
## <a name="getdeploymentdatafrommanifest"></a>GetDeploymentDataFromManifest  
 Bildirim ve etkinleştirme URL 'sinden dağıtım bilgilerini alır.  
  
### <a name="parameters"></a>Parametreler  
  
|Parametre|Açıklama|Tür|  
|---------------|-----------------|----------|  
|`pcwzActivationUrl`|İçin bir işaretçi `ActivationURL` .|LPCWSTR|  
|`pcwzPathToDeploymentManifest`|İçin bir işaretçi `PathToDeploymentManifest` .|LPCWSTR|  
|`pwzApplicationIdentity`|Döndürülen tam uygulama kimliğini belirten NULL ile sonlandırılmış bir dize almak için arabelleğin bir işaretçisi.|LPWSTR|  
|`pdwIdentityBufferLength`|Arabelleğin uzunluğu olan `pwzApplicationIdentity` , wchar cinsinden BIR DWORD işaretçisi. Buna NULL sonlandırma karakteri için boşluk dahildir.|LPDWORD|  
|`pwzProcessorArchitecture`|Bildirimden uygulama dağıtımının işlemci mimarisini belirten, NULL ile sonlandırılmış bir dize almak için arabellek işaretçisi.|LPWSTR|  
|`pdwArchitectureBufferLength`|Arabelleğin uzunluğu olan `pwzProcessorArchitecture` , wchar cinsinden BIR DWORD işaretçisi.|LPDWORD|  
|`pwzApplicationManifestCodebase`|Bildirimden uygulama bildiriminin kod temelini belirten NULL ile sonlandırılmış bir dize almak için arabellek işaretçisi.|LPWSTR|  
|`pdwCodebaseBufferLength`|Arabelleğin uzunluğu olan `pwzApplicationManifestCodebase` , wchar cinsinden BIR DWORD işaretçisi.|LPDWORD|  
|`pwzDeploymentProvider`|Varsa, bildirimden dağıtım sağlayıcısını belirten NULL ile sonlandırılmış bir dize almak için arabelleğin bir işaretçisi. Aksi takdirde, boş bir dize döndürülür.|LPWSTR|  
|`pdwProviderBufferLength`|Uzunluğu olan DWORD için bir işaretçi `pwzProviderBufferLength` .|LPDWORD|  
  
### <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa S_OK döndürür; Aksi takdirde, hatayı temsil eden bir HRESULT döndürür. Arabellek çok küçükse HRESULTFROMWIN32 (ERROR_INSUFFICIENT_BUFFER) döndürür.  
  
### <a name="remarks"></a>Açıklamalar  
 İşaretçiler null olmamalıdır. `pcwzActivationUrl` ve `pcwzPathToDeploymentManifest` boş olmamalıdır.  
  
 Etkinleştirme URL 'sini temizlemek çağıranın sorumluluğundadır. Örneğin, gerektiğinde kaçış karakterleri ekleme veya sorgu dizesini kaldırma.  
  
 Bu, giriş uzunluğunu sınırlamak için çağıranın sorumluluğundadır. Örneğin, URL uzunluğu en fazla 2 KB 'tır.  
  
## <a name="launchapplication"></a>LaunchApplication  
 Dağıtım URL 'SI kullanarak bir uygulamayı başlatır veya kurar.  
  
### <a name="parameters"></a>Parametreler  
  
|Parametre|Açıklama|Tür|  
|---------------|-----------------|----------|  
|`deploymentUrl`|Dağıtım bildiriminin URL 'sini içeren, NULL ile sonlandırılmış bir dize işaretçisi.|LPCWSTR|  
|`data`|Daha sonraki kullanımlar için ayrılmıştır. NULL olmalıdır.|LPVOıD|  
|`flags`|Daha sonraki kullanımlar için ayrılmıştır. 0 olmalıdır.|DWORD|  
  
### <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa S_OK döndürür; Aksi takdirde, hatayı temsil eden bir HRESULT döndürür. Yönetilen bir özel durum oluşursa, 0x80020009 (DISP_E_EXCEPTION) döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>
