<!DOCTYPE html>
<html>

<head>
	<base target="_top">
	<link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Mitr">
	<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/5.0.0-alpha1/css/bootstrap.min.css"
		integrity="sha384-r4NyP46KrjDleawBgD5tp8Y7UzmLA05oM1iAEQ17CSuDqnUK2+k9luXQOfXJCJ4I" crossorigin="anonymous">
	<!-- Font Awesome CSS -->
	<script src="https://kit.fontawesome.com/6a972cf3a7.js" crossorigin="anonymous"></script>
	<link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.8.1/css/all.css"
		integrity="sha384-50oBUHEmvpQ+1lW4y57PTFmhCaXp0ML5d60M1M7uH2+nqUivzIebhndOJK28anvf" crossorigin="anonymous">
	<style>
		body {
			font-family: "Mitr"
		}
	</style>
</head>

<body>
	<div class="container-fluid">

		<div class="row">
			<div class="col-md-auto mx-auto">

				<nav class="navbar navbar-expand-sm navbar-dark bg-danger flex-sm-nowrap flex-wrap">
					<div class="container-fluid">
						<button class="navbar-toggler flex-grow-sm-1 flex-grow-0 me-2" type="button" data-bs-toggle="collapse" data-bs-target="#navbar5">
            <span class="navbar-toggler-icon"></span>
        </button>
						<span class="navbar-brand flex-grow-1"><i class="far fa-address-card"></i> ฟอร์มบันทึกข้อมูล</span>
						<div class="navbar-collapse collapse flex-grow-1 justify-content-center" id="navbar5">
							<ul class="navbar-nav mx-auto">
								<li class="nav-item">
									<i class="fas fa-home mr-2"></i>กลับหน้าหลัก</a>
								</li>
							</ul>
						</div>
						<div class="flex-grow-1">
							<!--spacer-->
						</div>
					</div>
				</nav>

				<div class="card">
					<div class="card-header bg-info text-light">
						โรงเรียนอภิวัฒน์สอนสร้างสื่อ
					</div>
					<div class="card-body">

						<form class="main" id="form" novalidate="novalidate"
							style="max-width: 600px;margin: 20px auto;">
							<div id="forminner">
								<div class="form-row">
									<div class="form-group col-md-auto">
										<label for="id">เลขประจำตัวประชาชน</label>
										<input type="text area" class="form-control" id="id" name="id" maxlength="13" placeholder="เลขประจำตัวประชาชน">
                        </div>
										<div class="form-group col-md-auto">
											<label for="stdCode">เลขประจำตัวนักเรียน</label>
											<input type="text area" class="form-control" id="stdCode" name="stdCode" maxlength="6" placeholder="เลขประจำตัวนักเรียน">
                        </div>
											<div class="form-group col-md-auto">
												<label for="firstname">ชื่อ</label>
												<input type="text area" class="form-control" id="firstname" name="firstname" maxlength="80" placeholder="ชื่อ">
                        </div>
												<div class="form-group col-md-auto">
													<label for="lastname">นามสกุล</label>
													<input type="text area" class="form-control" id="lastname" name="lastname" maxlength="80" placeholder="นามสกุล">
                        </div>
													<div class="form-group col-md-auto">
														<label for="address">ที่อยู่</label>
														<input type="text area" class="form-control" id="address" name="address" maxlength="200" placeholder="ที่อยู่ปัจจุบัน">
                        </div>
														<div class="form-group col-md-auto">
															<label for="tel">เบอร์โทรศัพท์</label>
															<input type="text" class="form-control" id="tel" name="tel" maxlength="10" placeholder="xxx-xxxxxxx">
                        </div>
															<div class="form-group col-md-auto">
																<label for="email">อีเมล์</label>
																<input type="text" class="form-control" id="email" name="email" maxlength="50" placeholder="อีเมล์">
                        </div>

																<!--อัปโหลดรูภาพ-->
																<div class="row">
																	<div class="form-group col-md-auto">
																		<span>เลือกรูปภาพ</span>
																		<div class="btn">

																			<input id="files" type="file">
                        </div>
																		</div>
																	</div>
																	<div class="row justify-content-center">
																		<div class="input-field col s6 text-center">
																			<button type="submit" class="btn btn-danger mb-2" id="button" onclick="submitForm(); return false;">
                            บันทึกข้อมูล
                        </button>
																		</div>
																	</div>
																</div>

															</div>
						</form>

						<div >
							<div id="success" style="display:none">
								<h4 class="left-align teal-text">
									<center>
บันทึกข้อมูลเรียบร้อย!
									</center>
								</h4>

							</div>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
	</div>
	</div>
	<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.6.0/jquery.min.js"
		integrity="sha512-894YE6QWD5I59HgZOGReFYm4dnWc1Qt5NtvYSaNcOP+u1T9qYdvdihz0PPSiiqn/+/3e7Jo4EaG7TubfWGUrMQ=="
		crossorigin="anonymous"></script>
	<script src="https://cdnjs.cloudflare.com/ajax/libs/materialize/0.97.5/js/materialize.min.js"></script>

	<script>
        document.addEventListener('DOMContentLoaded', function () {
            var elems = document.querySelectorAll('select');
            var instances = M.FormSelect.init(elems);
        });
        var file, reader = new FileReader();
        reader.onloadend = function (e) {
            if (e.target.error != null) {
                showError("File " + file.name + " could not be read.");
                return;
            } else {
                google.script.run
                    .withSuccessHandler(showSuccess)
                    .uploadFile(e.target.result, file.name,
                        $('input#id').val(),
                        $('input#stdCode').val(),
                        $('input#firstname').val(),
                        $('input#lastname').val(),
                        $('input#address').val(),
                        $('input#tel').val(),
                        $('input#email').val()
                        
                    );
            }
        };
        function showSuccess(e) {
            if (e === "OK") {
                $('#forminner').hide();
                $('#success').show();
                $('#image').hide();
                
            } else {
                showError(e);
            }
        }
        function restartForm() {
            $('#form').trigger("reset");
            $('#forminner').show();
            $('#success').hide();
            $('#button').show();
        }
        
        function submitForm() {
            var id= $('input#id').val();
            if (id.length === 0) {
                showError("กรุณากรอกเลขประจำตัวประชาชน");
                return;
            }
            var stdCode = $('input#stdCode').val();
            if (stdCode.length === 0) {
                showError("กรุณากรอกเลขประจำตัวนักเรียน");
                return;
            }            
            var firstname = $('input#firstname').val();
            if (firstname.length === 0) {
                showError("กรุณากรอกชื่อ");
                return;
            }
            var lastname = $('input#lastname').val();
            if (lastname.length === 0) {
                showError("กรุณากรอกนามสกุล");
                return;
            }
            var add = $('input#address').val();
            if (add.length === 0) {
                showError("กรุณากรอกที่อยู่ปัจจุบัน");
                return;
            }
            var tel = $('input#tel').val();
            if (tel.length === 0) {
                showError("กรุณากรอกหมายเลขโทรศัพท์");
                return;
            }
            
            var files = $('#files')[0].files;
            if (files.length === 0) {
                showError("กรุณาเลือกไฟล์ภาพ");
                return;
            }
            document.getElementById("button").style.display = "none"
            file = files[0];
            if (file.size > 1024 * 1024 * 20) {
                showError("The file size should be < 20 MB. ");
                return;
            }
            showMessage("...ระบบกำลังบันทึกข้อมูล...");
            reader.readAsDataURL(file);
        }
        function showError(e) {
            Swal.fire({
                title: 'คุณกรอกข้อมูลยังไม่ครบ!',
                text: e,
                icon: 'error',
                confirmButtonText: 'ตกลง'
            })
        }
        function showMessage(e) {
            Swal.fire({
                title: '...กรุณารอสักครู...',
                text: '...ระบบกำลังบันทึกข้อมูล...',
                showConfirmButton: false,
              timer: 3000
            })
        }
        $(document).ready(function () {
            $('select').material_select();
        });
        document.getElementById("files").onchange = function () {
            var reader = new FileReader();
            reader.onload = function (e) {
                document.getElementById("image").src = e.target.result;
                $('#image').show();
            };
            reader.readAsDataURL(this.files[0]);
        };
	</script>
	<script src="//cdn.jsdelivr.net/npm/sweetalert2@10"></script>
</body>

</html>
