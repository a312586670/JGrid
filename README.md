# Examples for JGrid ���

Jquery.JGrid ��ҳ�б��������Կ�������ҳ����,�������֧�ֶ������
�򵥵Ļ�����ҳ����
------------
�򵥵��÷�ʽ
------------
```
var Grid1= $("#tt").Grid({
        method: 'GET',//�ύ��ʽGET|POST
        pageSize: 10,
        pageDetail:true,
        url: '/post/getdata',//������ԴUrl
        rows: [//������
            { width: '20%', field: 'name', title: '����', align: 'left' },
            { width: '15%', field: 'age', title: '����', align: 'left' },
            { width: '22%', field: 'school', title: '��ҵѧУ', align: 'left' },
            { width: '15%', field: 'address', title: '��ַ', align: 'left' },
            {
                width: '10%', field: 'states', title: '״̬', align: 'left',
                formatter: function (value, rowData) {
                    if (rowData.states == "1") {
                        return "������"
                    }
                    else {
                        return "��ͣ��"
                    }
                }
            },
            {
                width: '15%', field: 'states', title: 'ɾ��', align: 'left',
                formatter: function (value, rowData) {
                    if (rowData.states == "1") {
                        return "<a href='#' style='margin-right:10px;'>ɾ��</a>" +
                            "<a href='#' style='margin-right:10px;'>ͣ��</a>"
                    }
                    else {
                        return "<a href='#' style='margin-right:10px;'>ɾ��</a>" +
                           "<a href='#' style='margin-right:10px;'>����</a>"
                    }
                }
            }
        ]
    });

```
#Jquery.JGrid ֧��Post��Get��ʽ���ط�ҳ�б�ͬʱҲ֧�ֲ���ҳ�б����,֧�ֵ�����ģ�������������,ͨ���򵥵��������Լ���ʵ�����£���ϸ˵�����������Ե��ô�
------------
```
var grid=$("#id").Grid({
            order: "",//��������ʽ
            form: "form",//�����ID,����ʹ���ύ����ʽ���������ݵ���̨��Ҳ����ʹ�ò�����ʽ,�ο�dataParam����˵��
            dataParam:{key,value,key2,value,.....}//���ݵ���̨�Ĳ���
            method: "POST",//��������ģʽ
            width: "100%", //Ĭ��10%
            height: "auto",//�߶�Ĭ��auto
            page: 1, //�����ҳ��
            pageSize: 20,//ÿҳչʾ���ݵĴ�С
            showCheck: false,//�Ƿ���ʾ��ѡ��Ĭ��Ϊfalse
            showOrder: false,//�Ƿ�����Ĭ��false
            showRadio: false,//�Ƿ���ʾ��ѡ��,Ĭ��false(��showCheckֻ��ӵ��һ��)
            doubleLine: true,//�Ƿ���ʾ˫����ɫ,Ĭ��true
            pageDetail: false,//�Ƿ���ʾҳ������,Ĭ��false
            pagerCount: 10,//չʾҳ����pageDetailΪtrue��Ч
            isPager: true,//�Ƿ��ҳģʽ��Ĭ��true
            TotalPage: 0, //��ҳ����outPut(�������)
            Total: 0,   //�ܼ�¼��outPut(�������)
            Currpage: 0,//��ǰҳ��outPut(�������)
            rows: [],//����û�е���ϸ���,����������ʽ�����ݲ���,ʹ�õ�����ģ������ò������Ժ���
            dataType: "json",//������������Ĭ��Json��ʽ,��֧��jsonp��ʽ
            showNumber: true//�Ƿ���ʾ���
            url: "",  //����Դ��ַ
            key: "",//����������ʱ���Ժ���
            callback: callback,//�ص�����,ÿ�μ������ݺ�Ļص�����
            onClick: function () { },//�����¼�м������¼�
            isTemplate: false,//�Ƿ�Ϊģ�淽ʽ
            resolveTemplate: function(){},//ģ������������ݷ���,����ѽ���������ģ�淵�س�ȥ
            template: "",//ģ��
            noneData:""//û������ʱչʾ����Ϣ
})
```
# ����˵��:

Grid ��ʼ���б�����
------------
```
$("#id").Grid(setting,callback)//����,��һ������Ϊ������Ϣ,�ڶ�������Ϊ�ص�����
```
reLoad ����:
------------
```
$("#id").reLoad(setting)//�÷�����������ˢ�����ݷ��������԰�setting�������´��ݽ�ȥ,����ʵ�������ȹ���
```

����ǰ������grid�������������ʵ���������ܣ�
------------
```
var option = {    
    enabled: $("#pageType2").val(),//�����Ĳ���һ    
    name: $("#pageName2").val(),    //�����Ĳ�����
    scope: 1    
}    
grid.reLoad(option);
```

Refresh����:

var option = {    
    dataParam:{
        enabled: $("#pageType2").val(),//�����Ĳ���һ    
        name: $("#pageName2").val(),    //�����Ĳ�����
        scope: 1  
    } 
}    
grid.Refresh(option);