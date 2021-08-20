---
title: ClickOnce Unmanaged API Reference | Microsoft Docs
description: CleanOnlineAppCache ClickOnce, GetDeploymentDataFromManifest ve LaunchApplication dahil olmak üzere dfshim.dll'den gelen genel API'ler hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
api_name:
- CleanOnlineAppCache
- GetDeploymentDataFromManifest
- LaunchApplication
api_location:
- dfshim.dll
api_type:
- COM
topic_type:
- apiref
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- cplusplus
ms.openlocfilehash: c78c5dc002caaa17569d3a71f01aa47e7ae901c1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073870"
---
# <a name="clickonce-unmanaged-api-reference"></a>ClickOnce api başvurusu
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dfshim.dll'den genel API'leri dfshim.dll.

## <a name="cleanonlineappcache"></a>CleanOnlineAppCache
 Tüm çevrimiçi uygulamaları uygulama önbelleğinden temizler [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] veya kaldırır.

### <a name="return-value"></a>Döndürülen değer
 Başarılı olursa, S_OK; aksi takdirde, hatayı temsil eden bir HRESULT döndürür. Yönetilen bir özel durum oluşursa, 0x80020009 (DISP_E_EXCEPTION).

### <a name="remarks"></a>Açıklamalar
 CleanOnlineAppCache çağrısı, henüz [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] çalışmıyorsa hizmeti başlatacak.

## <a name="getdeploymentdatafrommanifest"></a>GetDeploymentDataFromManifest
 Bildirim ve etkinleştirme URL'lerinden dağıtım bilgilerini alın.

### <a name="parameters"></a>Parametreler

|Parametre|Açıklama|Tür|
|---------------|-----------------|----------|
|`pcwzActivationUrl`|`ActivationURL`işaretçisi.|LPCWSTR|
|`pcwzPathToDeploymentManifest`|`PathToDeploymentManifest`işaretçisi.|LPCWSTR|
|`pwzApplicationIdentity`|Döndürülen tam uygulama kimliğini belirten NULL sonlandırıldı dizesini almak için bir arabelleğe işaretçi.|Lpwstr|
|`pdwIdentityBufferLength`|WCHAR'lar içinde arabelleğin uzunluğu olan bir DWORD `pwzApplicationIdentity` işaretçisi. Bu, NULL sonlandırma karakteri için alanı içerir.|LPDWORD|
|`pwzProcessorArchitecture`|Bildirimden uygulama dağıtımının işlemci mimarisini belirten NULL sonlandırıldı dizesini almak için bir arabelleğe işaretçi.|Lpwstr|
|`pdwArchitectureBufferLength`|WCHAR'lar içinde arabelleğin uzunluğu olan bir DWORD `pwzProcessorArchitecture` işaretçisi.|LPDWORD|
|`pwzApplicationManifestCodebase`|Bildirimden uygulama bildiriminin kod tabanını belirten NULL sonlandırıldı dizesini almak için arabelleğe işaretçi.|Lpwstr|
|`pdwCodebaseBufferLength`|WCHAR'lar içinde arabelleğin uzunluğu olan bir DWORD `pwzApplicationManifestCodebase` işaretçisi.|LPDWORD|
|`pwzDeploymentProvider`|Varsa, bildirimden dağıtım sağlayıcısını belirten NULL sonlandırıldı dizesini almak için bir arabelleğe işaretçi. Aksi takdirde boş bir dize döndürülür.|Lpwstr|
|`pdwProviderBufferLength`|uzunluğu olan bir DWORD `pwzProviderBufferLength` işaretçisi.|LPDWORD|

### <a name="return-value"></a>Döndürülen değer
 Başarılı olursa, S_OK; aksi takdirde, hatayı temsil eden bir HRESULT döndürür. Arabellek çok küçükse HRESULTFROMWIN32(ERROR_INSUFFICIENT_BUFFER) döndürür.

### <a name="remarks"></a>Açıklamalar
 İşaretçiler null olmamalıdır. `pcwzActivationUrl` ve `pcwzPathToDeploymentManifest` boş olamaz.

 Etkinleştirme URL'sini temizlemek çağıranın sorumluluğundadır. Örneğin, gerekli olduğu yere kaçış karakterleri ekleme veya sorgu dizesini kaldırma.

 Giriş uzunluğunu sınırlamak çağıranın sorumluluğundadır. Örneğin, maksimum URL uzunluğu 2 KB'tir.

## <a name="launchapplication"></a>LaunchApplication
 Dağıtım URL'si kullanarak bir uygulamayı başlatıyor veya yüklür.

### <a name="parameters"></a>Parametreler

|Parametre|Açıklama|Tür|
|---------------|-----------------|----------|
|`deploymentUrl`|Dağıtım bildiriminin URL'sini içeren NULL ile sonlandırılan dizenin işaretçisi.|LPCWSTR|
|`data`|Daha sonraki kullanımlar için ayrılmıştır. NULL olmalıdır.|LPVOID|
|`flags`|Daha sonraki kullanımlar için ayrılmıştır. 0 olması gerekir.|DWORD|

### <a name="return-value"></a>Döndürülen değer
 Başarılı olursa, S_OK; aksi takdirde, hatayı temsil eden bir HRESULT döndürür. Yönetilen bir özel durum oluşursa, 0x80020009 (DISP_E_EXCEPTION).

## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>