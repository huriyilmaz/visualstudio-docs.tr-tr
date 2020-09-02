---
title: SccEndBatch Işlevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 986056b1f5202c2fb94d27a8792ed3b0fe308944
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200135"
---
# <a name="sccendbatch-function"></a>SccEndBatch İşlevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu işlev, kaynak denetimi işlemlerinin bir toplu işlemini sonlanır. Bu toplu işlemler iç içe olamaz.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
SCCRTN SccEndBatch(void);  
```  
  
#### <a name="parameters"></a>Parametreler  
 Yok.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|SCC_OK|Toplu işlem başarıyla sonuçlandırdı.|  
|SCC_E_UNKNOWNERROR|Özel olmayan hata.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kaynak denetimi toplu işleri, birden çok proje veya birden çok bağlam arasında aynı kaynak denetimi işlemlerini yürütmek için kullanılır. Toplu işlem sırasında Kullanıcı deneyiminden gereksiz iletişim kutularını ortadan kaldırmak için toplu işlemler kullanılabilir. [SccBeginBatch](../extensibility/sccbeginbatch-function.md) ve `SccEndBatch` işlevi bir işlemin başlangıcını ve sonunu belirtmek için bir çift olarak kullanılır. Bunlar iç içe geçirilemez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak denetimi eklentisi API Işlevleri](../extensibility/source-control-plug-in-api-functions.md)   
 [SccBeginBatch](../extensibility/sccbeginbatch-function.md)
