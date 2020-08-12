---
title: 'IDispatchEx:: Getnextdıspıd | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetNextDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetNextDispID method
ms.assetid: 8263d441-85ee-47f4-bdba-fbf2ad07e85f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8811e828a6701769badf45ca7c37f9c53529150f
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144435"
---
# <a name="idispatchexgetnextdispid"></a>IDispatchEx::GetNextDispID

Nesnesinin üyelerini numaralandırır.

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT GetNextDispID(
   DWORD grfdex,
   DISPID id,
   DISPID *pid
);
```

## <a name="parameters"></a>Parametreler

`grfdex`\
Hangi öğe kümesinin numaralandırılacağını belirler. Bu, aşağıdaki değerlerin bir birleşimi olabilir:

|Değer|Anlamı|
|-----------|-------------|
|fdexEnumDefault|Nesnenin varsayılan öğeleri numaralandırır. Nesnenin herhangi bir öğe kümesini numaralandırması için izin verilir.|
|fdexEnumAll|Nesnenin tüm öğeleri numaralandırır. Nesnenin herhangi bir öğe kümesini numaralandırması için izin verilir.|

`id`\
Geçerli üyeyi tanımlar. Getnextdıspıd bundan sonra Numaralandırmadaki öğeyi alır. Bu tanımlayıcıyı almak için Getdıspıd veya bir önceki Getnextdıspıd çağrısını kullanır. İlk öğenin ilk tanımlayıcısını almak için DISPID_STARTENUM değerini kullanır.

`pid`\
Numaralandırmadaki bir sonraki öğenin tanımlayıcısını alan bir DISPID değişkeninin adresi.

Bir üye veya tarafından silinirse `DeleteMemberByName` `DeleteMemberByDispID` , `DISPID` için geçerli kalması gerekir `GetNextDispID` .

## <a name="return-value"></a>Dönüş Değeri

Aşağıdaki değerlerden birini döndürür:

|Değer|Anlamı|
|-|-|
|`S_OK`|Başarılı.|
|`S_FALSE`|Sabit listesi bitti.|

## <a name="example"></a>Örnek

```cpp
   HRESULT hr;
   BSTR bstrName;
   DISPID dispid;
   IDispatchEx *pdex;

   // Assign to pdex
   hr = pdex->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);
   while (hr == NOERROR)
   {
      hr = pdex->GetMemberName(dispid, &bstrName);
      if (!wcscmp(bstrName, OLESTR("Bar")))
      {
         SysFreeString(bstrName);
         return TRUE;
      }
      SysFreeString(bstrName);
      hr = pdex->GetNextDispID(fdexEnumAll, dispid, &dispid);
   }
```

## <a name="see-also"></a>Ayrıca bkz.

- [IDispatchEx Arabirimi](../../winscript/reference/idispatchex-interface.md)
- [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)
- [IDispatchEx::DeleteMemberByName](../../winscript/reference/idispatchex-deletememberbyname.md)
- [IDispatchEx::DeleteMemberByDispID](../../winscript/reference/idispatchex-deletememberbydispid.md)