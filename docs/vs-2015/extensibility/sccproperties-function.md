---
title: SccProperties Işlevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f4e8452465873cb66883abd347406d17b469e90a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199995"
---
# <a name="sccproperties-function"></a>SccProperties İşlevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu işlev, bir dosya veya proje için kaynak denetimi özelliklerini görüntüler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
SCCRTN SccProperties (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 pvContext  
 'ndaki Kaynak denetimi eklentisi bağlam yapısı.  
  
 lendiği  
 'ndaki Kaynak denetimi eklentisinin, sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi için bir işleyici.  
  
 lpFileName  
 'ndaki Dosyanın veya projenin tam yol adı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|SCC_OK|Özellikler başarıyla görüntülendi.|  
|SCC_I_RELOADFILE|Sürüm denetim sistemi dosya özelliklerini değiştirdi, bu nedenle IDE 'nin bu dosyayı yeniden yüklemesi gerekir.|  
|SCC_E_PROJNOTOPEN|Belirtilen proje kaynak denetiminde açılmadı.|  
|SCC_E_NOTAUTHORIZED|Kullanıcının bu dosyanın veya projenin özelliklerini görüntüleme yetkisi yok.|  
|SCC_E_FILENOTCONTROLLED|Belirtilen dosya veya proje kaynak denetimi altında değil.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Bilinmeyen veya genel bir hata oluştu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kaynak denetimi eklentisi, özellikleri kendi iletişim kutusunda görüntüler.  
  
 Özellikler kaynak denetimi eklentisi tarafından tanımlanır ve eklentilerden farklı olabilir. Eklenti, kullanıcının bir dosyanın kaynak denetimi özelliklerini değiştirmesine izin veriyorsa, `SCC_I_RELOAD` Bu dosya veya projenin yeniden yüklenmesi gereken IDE 'yi işaret etmesi için döndürmelidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
