---
title: SccDirQueryInfo Işlevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7334ddd1ce6c7f9feac63253246e55b65121e18b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64780267"
---
# <a name="sccdirqueryinfo-function"></a>SccDirQueryInfo İşlevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu işlev, geçerli durumları için tam dizinlerin listesini inceler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
SCCRTN SccDirQueryInfo(  
LPVOID  pContext,  
LONG    nDirs,  
LPCSTR* lpDirNames,  
LPLONG  lpStatus  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 pContext  
 'ndaki Kaynak denetimi eklentisi bağlam yapısı.  
  
 nDirs  
 'ndaki Sorgulanmasını seçtiğiniz dizinlerin sayısı.  
  
 lpDirNames  
 'ndaki Sorgulanacak dizinlerin tam nitelikli yolları dizisi.  
  
 lpStatus  
 [in, out] Kaynak denetimi eklentisinin durum bayraklarını döndürmesi için bir dizi yapısı (Ayrıntılar için [Dizin durum koduna](../extensibility/directory-status-code-enumerator.md) bakın).  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|SCC_OK|Sorgu başarılı oldu.|  
|SCC_E_OPNOTSUPPORTED|Kaynak kodu denetim sistemi bu işlemi desteklemiyor.|  
|SCC_E_ACCESSFAILURE|Büyük olasılıkla ağ veya çekişme sorunlarından dolayı kaynak denetim sistemine erişirken bir sorun oluştu. Yeniden deneme önerilir.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Özel olmayan hata.|  
  
## <a name="remarks"></a>Açıklamalar  
 İşlevi, döndürülen diziyi aileden bit bit maskesi `SCC_DIRSTATUS` (bkz. [Dizin durum kodu](../extensibility/directory-status-code-enumerator.md)), verilen her dizin için bir giriş ile doldurur. Durum dizisi, çağıran tarafından ayrılır.  
  
 Bu işlev, bir dizin yeniden adlandırılmadan önce, kaynağın karşılık gelen bir proje olup olmadığını sorgulayarak kaynak denetimi altında olup olmadığını denetlemek için kullanılır. Dizin, kaynak denetimi altında değilse, IDE kullanıcıya uygun bir uyarı verebilir.  
  
> [!NOTE]
> Bir kaynak denetimi eklentisi bir veya daha fazla durum değeri uygulamamı seçerse, uygulanmayan bitler sıfır olarak ayarlanmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak denetimi eklentisi API Işlevleri](../extensibility/source-control-plug-in-api-functions.md)   
 [Dizin Durumu Kodu](../extensibility/directory-status-code-enumerator.md)
