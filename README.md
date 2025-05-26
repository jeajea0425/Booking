# Booking
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>订餐服务</title>
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
</head>
<body>
    <div class="container">
        <h1>订餐服务</h1>
        <form id="diningForm">
            <div class="form-group">
                <label for="customerName">客户姓名</label>
                <input type="text" class="form-control" id="customerName" required>
            </div>
            <div class="form-group">
                <label for="contactInfo">联系方式</label>
                <input type="text" class="form-control" id="contactInfo" required>
            </div>
            <div class="form-group">
                <label for="menuName">菜品名称</label>
                <select class="form-control" id="menuName">
                    <option value="宫保鸡丁">宫保鸡丁</option>
                    <option value="鱼香肉丝">鱼香肉丝</option>
                    <option value="红烧肉">红烧肉</option>
                </select>
            </div>
            <div class="form-group">
                <label for="orderTime">订餐时间</label>
                <input type="datetime-local" class="form-control" id="orderTime" required>
            </div>
            <button type="submit" class="btn btn-primary">提交订餐</button>
        </form>
    </div>
    <script>
        document.getElementById('diningForm').addEventListener('submit', function(event) {
            event.preventDefault();
            const customerName = document.getElementById('customerName').value;
            const contactInfo = document.getElementById('contactInfo').value;
            const menuName = document.getElementById('menuName').value;
            const orderTime = document.getElementById('orderTime').value;

            fetch('/api/diningOrders', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify({
                    customerName,
                    contactInfo,
                    menuName,
                    orderTime
                })
            }).then(response => response.json())
              .then(data => {
                  alert('订餐成功！');
                  console.log(data);
              });
        });
    </script>
</body>
</html>
