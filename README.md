<!DOCTYPE html>
<html>

	<head>
		<meta charset="UTF-8">
		<title></title>
		<script src="js/jquery.min.js" type="text/javascript"></script>
		<script>
			function uploadclick(file) {
				var form = new FormData();

				form.append("fileImg", file.files);

				$.ajax({
					type: "post",
					url: "传输的地址",
					data: form,
					contentType: false, // 注意这里应设为false
					processData: false, //false
					cache: false, //缓存
					success: function(data) {
						console.log(data);
					}
				})
			}
			$("#wholeImg").click(function() {
				$("#whole").click();
			})

			function previewImg(file) {
				//判断是否支持FileReader
				if(window.FileReader) {
					var reader = new FileReader();
				} else {
					alert("您的设备不支持图片预览功能，如需该功能请升级您的设备！");
				}
				var preDiv = document.getElementById("wholeImg");
				//获取图片
				if(file.files && file.files[0]) {
					var reader = new FileReader();
					reader.onload = function(e) {
						var img = document.getElementById("img1");
						img.setAttribute("src", e.target.result);
					}
					reader.readAsDataURL(file.files[0]);
				}
			}
		</script>
	</head>

	<body>
		<form id="formTest">
			<input type="text" name="name1" />
			<input type="text" name="name2" />
			<input type="file" name="file" id="file" />
		</form>
		<div class="pic" id="wholeImg">
			<img id="img1" src="img/a11.png" />
		</div>
		<input type="file" name="whole" id="whole" style="display: none;" capture="camera" onchange="previewImg(this)" />
	</body>

</html>
//=>>	https://www.cnblogs.com/dealblog/p/7760554.html
