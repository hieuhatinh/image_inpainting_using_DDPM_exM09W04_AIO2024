# Image Inpaiting using Denoising Diffusion Probabilistic Model - Exercise M09W04

**Diffusion Models** là một trong những mô hình sinh ngày càng được ứng dụng rộng rãi cho nhiều ứng dụng khác nhau như: Image Inpainting (Chỉnh sửa hình ảnh khuyết thiếu), Image Colorization (Tô màu hình ảnh),... Diffusion Models có nhiệm vụ tạo ra một phân phối cho dữ liệu đầu vào và xấp xỉ phân phối của dữ liệu được sinh ra với phân phối của dữ liệu gốc, từ đó giúp mô hình có thể sinh ra hình ảnh mới.

Diffusion Models bao gồm 2 quá trình: Forward Diffusion Process và Reverse Diffusion Process được mô tả như hình sau:

![Pipeline Diffusion Model](/readme_img/ddpm_pipeline.png 'AIO2024')

***Forward Diffusion Process (FDP):*** Từ một điểm dữ liệu đầu vào x0 thuộc một phân phối biết trước x0 ∼ q(x), FDP sẽ thêm từ từ lần lượt theo thời gian một lượng nhỏ nhiễu được lấy mẫu từ phân phối Gauss ϵ ∼ N(µ,σ2) tạo ra các mẫu chứa nhiễu $x_1, x_2, ..., x_T$ với T (steps) số bước thêm nhiễu vào.

***Reverse Diffusion Process (RDP):*** Tại thời điểm $x_T$ là mẫu chứa nhiễu, RDF sẽ tiến hành huấn luyện mô hình để khử nhiễu, khôi phục lại dữ liệu hình ảnh đầu vào. Mô hình được sử dụng trong quá trình decode khử nhiễu là UNet kết hợp với cơ chế Attention.