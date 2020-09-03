---
title: SccEnumChangedFiles Işlevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 00ef98c93f02aa8e8a1b4ea53f1998d0ab6713a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200123"
---
# <a name="sccenumchangedfiles-function"></a>SccEnumChangedFiles İşlevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yerel dosyaların listesi verildiğinde, bu işlev kaynak kodu denetim veritabanındaki ilgili sürümlerden farklı olan dosyaları belirler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
SCCRTN SccEnumChangedFiles(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LONG    cFiles,  
   LPCSTR* lpFileNames,  
   LONG*   plIsFileDifferent  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 pContext  
 'ndaki Kaynak denetimi eklentisi bağlam işaretçisi.  
  
 lendiği  
 'ndaki Kaynak denetimi eklentisinin, sağladığı tüm iletişim kutuları için üst öğe olarak kullanabileceği IDE penceresi için bir işleyici.  
  
 cFiles  
 'ndaki Dizide belirtilen dosya adı sayısı `lpFileNames` . Ayrıca dizinin boyutunu belirtir `plIsFileDifferent` .  
  
 lpDosyaAdı  
 'ndaki Denetlenecek yerel dosya adları dizisi.  
  
 Plisfilefarklı  
 [in, out] Her dosyanın fark durumunu gösteren değerler dizisi (dizi en az girişe sahip olmalıdır `cFiles` ). Sıfır dışında, dosyanın farklı olduğu anlamına gelir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|SCC_OK|İşlem başarıyla tamamlandı.|  
|SCC_UNSPECIFIEDERROR|Genel hata.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
