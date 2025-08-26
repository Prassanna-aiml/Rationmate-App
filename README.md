# Rationmate-App
An inclusive ration management app with a clean HTML5 &amp; Tailwind CSS front-end, optimized for low-end devices and multilingual support. Built with React.js for a responsive and scalable backend, the app enhances accessibility, transparency, and usability, offering real-time tracking of entitlements.

<!DOCTYPE html>
<html>
<head>
    <link rel="preconnect" href="https://fonts.gstatic.com/" crossorigin="" />
    <link
      rel="stylesheet"
      as="style"
      onload="this.rel='stylesheet'"
      href="https://fonts.googleapis.com/css2?display=swap&amp;family=Manrope%3Awght%40400%3B500%3B700%3B800&amp;family=Noto+Sans%3Awght%40400%3B500%3B700%3B900"
    />
    <title>Ration Management System</title>
    <link rel="icon" type="image/x-icon" href="data:image/x-icon;base64," />
    <script src="https://cdn.tailwindcss.com?plugins=forms,container-queries"></script>
    <style>
        .page {
            display: none;
        }
        .page.active {
            display: block;
        }
        .fade-in {
            animation: fadeIn 0.3s ease-in;
        }
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            background: #53d22c;
            color: #131712;
            padding: 12px 20px;
            border-radius: 8px;
            font-weight: bold;
            z-index: 1000;
            transform: translateX(400px);
            transition: transform 0.3s ease;
        }
        .notification.show {
            transform: translateX(0);
        }
        .delete-btn {
            background: #ef4444;
            color: white;
            transition: all 0.2s ease;
        }
        .delete-btn:hover {
            background: #dc2626;
            transform: scale(1.05);
        }
        .confirm-modal {
            background: rgba(0, 0, 0, 0.7);
            backdrop-filter: blur(4px);
        }
    </style>
</head>
<body>
    <div class="relative flex size-full min-h-screen flex-col bg-[#131712] dark group/design-root overflow-x-hidden" style='font-family: Manrope, "Noto Sans", sans-serif;'>
        
        <!-- Page 1: Welcome/Login Selection -->
        <div id="page1" class="page active">
            <div class="layout-container flex h-full grow flex-col">
                <header class="flex items-center justify-between whitespace-nowrap border-b border-solid border-b-[#2d372a] px-10 py-3">
                    <div class="flex items-center gap-4 text-white">
                        <div class="size-4">
                            <svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path d="M24 45.8096C19.6865 45.8096 15.4698 44.5305 11.8832 42.134C8.29667 39.7376 5.50128 36.3314 3.85056 32.3462C2.19985 28.361 1.76794 23.9758 2.60947 19.7452C3.451 15.5145 5.52816 11.6284 8.57829 8.5783C11.6284 5.52817 15.5145 3.45101 19.7452 2.60948C23.9758 1.76795 28.361 2.19986 32.3462 3.85057C36.3314 5.50129 39.7376 8.29668 42.134 11.8833C44.5305 15.4698 45.8096 19.6865 45.8096 24L24 24L24 45.8096Z" fill="currentColor"></path>
                            </svg>
                        </div>
                        <h2 class="text-white text-lg font-bold leading-tight tracking-[-0.015em]">RationMate</h2>
                    </div>
                </header>
                <div class="px-40 flex flex-1 justify-center py-5">
                    <div class="layout-content-container flex flex-col w-[512px] max-w-[512px] py-5 max-w-[960px] flex-1">
                        <h2 class="text-white tracking-light text-[28px] font-bold leading-tight px-4 text-center pb-3 pt-5">Welcome to RationMate</h2>
                        <div class="flex justify-center">
                            <div class="flex flex-1 gap-3 max-w-[480px] flex-col items-stretch px-4 py-3">
                                <button id="loginUser" class="flex min-w-[84px] max-w-[480px] cursor-pointer items-center justify-center overflow-hidden rounded-full h-12 px-5 bg-[#53d22c] text-[#131712] text-base font-bold leading-normal tracking-[0.015em] w-full">
                                    <span class="truncate">Login as User</span>
                                </button>
                                <button id="loginShopOwner" class="flex min-w-[84px] max-w-[480px] cursor-pointer items-center justify-center overflow-hidden rounded-full h-12 px-5 bg-[#2d372a] text-white text-base font-bold leading-normal tracking-[0.015em] w-full">
                                    <span class="truncate">Login as Shop Owner</span>
                                </button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Page 2: Shop Selection -->
        <div id="page2" class="page">
            <div class="layout-container flex h-full grow flex-col">
                <header class="flex items-center justify-between whitespace-nowrap border-b border-solid border-b-[#2d372a] px-10 py-3">
                    <div class="flex items-center gap-4 text-white">
                        <div class="size-4">
                            <svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path d="M24 45.8096C19.6865 45.8096 15.4698 44.5305 11.8832 42.134C8.29667 39.7376 5.50128 36.3314 3.85056 32.3462C2.19985 28.361 1.76794 23.9758 2.60947 19.7452C3.451 15.5145 5.52816 11.6284 8.57829 8.5783C11.6284 5.52817 15.5145 3.45101 19.7452 2.60948C23.9758 1.76795 28.361 2.19986 32.3462 3.85057C36.3314 5.50129 39.7376 8.29668 42.134 11.8833C44.5305 15.4698 45.8096 19.6865 45.8096 24L24 24L24 45.8096Z" fill="currentColor"></path>
                            </svg>
                        </div>
                        <h2 class="text-white text-lg font-bold leading-tight tracking-[-0.015em]">Ration System</h2>
                    </div>
                    <div class="flex flex-1 justify-end gap-8">
                        <div class="flex items-center gap-9">
                            <a class="text-white text-sm font-medium leading-normal cursor-pointer" onclick="showPage('page1')">Home</a>
                            <a class="text-white text-sm font-medium leading-normal" href="#">About</a>
                            
                        </div>
                        <button onclick="showPage('page1')" class="flex min-w-[84px] max-w-[480px] cursor-pointer items-center justify-center overflow-hidden rounded-full h-10 px-4 bg-[#2d372a] text-white text-sm font-bold leading-normal tracking-[0.015em]">
                            <span class="truncate">Back to Home</span>
                        </button>
                        <div class="bg-center bg-no-repeat aspect-square bg-cover rounded-full size-10" style='background-image: url("https://lh3.googleusercontent.com/aida-public/AB6AXuBpqr0SSnW1O15H9qWp2DZp5rha02aFAoU4pSxipe-lJQmtdgH8Mo_jEbRfw2764l3Tj-kClC5ET3mmk_kmK8FTK34m2yDo4SN72fZetJgKBaU7qIYOW6E7SPBtpLwCBOfQVeXfM5goUpPHqi1IgmJMvTQSF4J-Qw8bBkWHeXuupXYyD-8qB7gMFDjRZO56LhZ1uIL3UZyEOf5-o4uNZeIOUMFxN6dORSKTY8OzPNcwfgpvg_HtoHeiVeFCiUN__oDbomQLZXLRQAo");'></div>
                    </div>
                </header>
                <div class="px-40 flex flex-1 justify-center py-5">
                    <div class="layout-content-container flex flex-col max-w-[960px] flex-1">
                        <div class="flex flex-wrap justify-between gap-3 p-4">
                            <p class="text-white tracking-light text-[32px] font-bold leading-tight min-w-72">Select Your Shop</p>
                        </div>
                        
                        <!-- Shop Password Modal -->
                        <div id="passwordModal" class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50" style="display: none;">
                            <div class="bg-[#1f251d] p-8 rounded-xl border border-[#42513e] max-w-md w-full mx-4">
                                <h3 class="text-white text-xl font-bold mb-4">Enter Shop Password</h3>
                                <input id="shopPassword" type="password" placeholder="Enter password" class="form-input flex w-full min-w-0 flex-1 resize-none overflow-hidden rounded-xl text-white focus:outline-0 focus:ring-0 border border-[#42513e] bg-[#131712] focus:border-[#42513e] h-14 placeholder:text-[#a5b6a0] p-[15px] text-base font-normal leading-normal mb-4">
                                <div class="flex gap-3">
                                    <button id="verifyPassword" class="flex-1 cursor-pointer items-center justify-center overflow-hidden rounded-full h-10 px-4 bg-[#53d22c] text-[#131712] text-sm font-bold leading-normal tracking-[0.015em]">
                                        Login
                                    </button>
                                    <button id="cancelPassword" class="flex-1 cursor-pointer items-center justify-center overflow-hidden rounded-full h-10 px-4 bg-[#2d372a] text-white text-sm font-bold leading-normal tracking-[0.015em]">
                                        Cancel
                                    </button>
                                </div>
                            </div>
                        </div>

                        <div class="p-4 cursor-pointer shop-item" data-shop="1">
                            <div class="flex items-stretch justify-between gap-4 rounded-xl hover:bg-[#1f251d] p-4 transition-colors">
                                <div class="flex flex-col gap-1 flex-[2_2_0px]">
                                    <p class="text-white text-base font-bold leading-tight">Shop 1:Tambaram Ration</p>
                                    <p class="text-[#a5b6a0] text-sm font-normal leading-normal"> Main Street, Tambaram</p>
                                </div>
                                <div class="w-full bg-center bg-no-repeat aspect-video bg-cover rounded-xl flex-1" style='background-image: url("https://media.assettype.com/TNIE%2Fimport%2F2019%2F2%2F17%2Foriginal%2FRation_Shops.jpg?w=480&auto=format%2Ccompress");'></div>
                            </div>
                        </div>
                        
                        <div class="p-4 cursor-pointer shop-item" data-shop="2">
                            <div class="flex items-stretch justify-between gap-4 rounded-xl hover:bg-[#1f251d] p-4 transition-colors">
                                <div class="flex flex-col gap-1 flex-[2_2_0px]">
                                    <p class="text-white text-base font-bold leading-tight">Shop 2:Perambur Ration </p>
                                    <p class="text-[#a5b6a0] text-sm font-normal leading-normal"> Central Avenue, Perambur</p>
                                </div>
                                <div class="w-full bg-center bg-no-repeat aspect-video bg-cover rounded-xl flex-1" style='background-image: url("https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTs1Vg8KyqPFSomEU3IJJm8CvsYSlUKwm8GfA&s");'></div>
                            </div>
                        </div>
                        
                        <div class="p-4 cursor-pointer shop-item" data-shop="3">
                            <div class="flex items-stretch justify-between gap-4 rounded-xl hover:bg-[#1f251d] p-4 transition-colors">
                                <div class="flex flex-col gap-1 flex-[2_2_0px]">
                                    <p class="text-white text-base font-bold leading-tight">Shop 3:Kundrathur  Ration </p>
                                    <p class="text-[#a5b6a0] text-sm font-normal leading-normal">Gandhi Nagar,Kundrathur</p>
                                </div>
                                <div class="w-full bg-center bg-no-repeat aspect-video bg-cover rounded-xl flex-1" style='background-image: url("https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcR0AphCmgma7q2CcXYcx0tTHU9SgnqEsE02DQ&s");'></div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Page 3: Shop Inventory Management -->
        <div id="page3" class="page">
            <div class="layout-container flex h-full grow flex-col">
                <header class="flex items-center justify-between whitespace-nowrap border-b border-solid border-b-[#2d372a] px-10 py-3">
                    <div class="flex items-center gap-4 text-white">
                        <div class="size-4">
                            <svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path d="M13.8261 30.5736C16.7203 29.8826 20.2244 29.4783 24 29.4783C27.7756 29.4783 31.2797 29.8826 34.1739 30.5736C36.9144 31.2278 39.9967 32.7669 41.3563 33.8352L24.8486 7.36089C24.4571 6.73303 23.5429 6.73303 23.1514 7.36089L6.64374 33.8352C8.00331 32.7669 11.0856 31.2278 13.8261 30.5736Z" fill="currentColor"></path>
                                <path fill-rule="evenodd" clip-rule="evenodd" d="M39.998 35.764C39.9944 35.7463 39.9875 35.7155 39.9748 35.6706C39.9436 35.5601 39.8949 35.4259 39.8346 35.2825C39.8168 35.2403 39.7989 35.1993 39.7813 35.1602C38.5103 34.2887 35.9788 33.0607 33.7095 32.5189C30.9875 31.8691 27.6413 31.4783 24 31.4783C20.3587 31.4783 17.0125 31.8691 14.2905 32.5189C12.0012 33.0654 9.44505 34.3104 8.18538 35.1832C8.17384 35.2075 8.16216 35.233 8.15052 35.2592C8.09919 35.3751 8.05721 35.4886 8.02977 35.589C8.00356 35.6848 8.00039 35.7333 8.00004 35.7388C8.00004 35.739 8 35.7393 8.00004 35.7388C8.00004 35.7641 8.0104 36.0767 8.68485 36.6314C9.34546 37.1746 10.4222 37.7531 11.9291 38.2772C14.9242 39.319 19.1919 40 24 40C28.8081 40 33.0758 39.319 36.0709 38.2772C37.5778 37.7531 38.6545 37.1746 39.3151 36.6314C39.9006 36.1499 39.9857 35.8511 39.998 35.764ZM4.95178 32.7688L21.4543 6.30267C22.6288 4.4191 25.3712 4.41909 26.5457 6.30267L43.0534 32.777C43.0709 32.8052 43.0878 32.8338 43.104 32.8629L41.3563 33.8352C43.104 32.8629 43.1038 32.8626 43.104 32.8629L43.1051 32.865L43.1065 32.8675L43.1101 32.8739L43.1199 32.8918C43.1276 32.906 43.1377 32.9246 43.1497 32.9473C43.1738 32.9925 43.2062 33.0545 43.244 33.1299C43.319 33.2792 43.4196 33.489 43.5217 33.7317C43.6901 34.1321 44 34.9311 44 35.7391C44 37.4427 43.003 38.7775 41.8558 39.7209C40.6947 40.6757 39.1354 41.4464 37.385 42.0552C33.8654 43.2794 29.133 44 24 44C18.867 44 14.1346 43.2794 10.615 42.0552C8.86463 41.4464 7.30529 40.6757 6.14419 39.7209C4.99695 38.7775 3.99999 37.4427 3.99999 35.7391C3.99999 34.8725 4.29264 34.0922 4.49321 33.6393C4.60375 33.3898 4.71348 33.1804 4.79687 33.0311C4.83898 32.9556 4.87547 32.8935 4.9035 32.8471C4.91754 32.8238 4.92954 32.8043 4.93916 32.7889L4.94662 32.777L4.95178 32.7688ZM35.9868 29.004L24 9.77997L12.0131 29.004C12.4661 28.8609 12.9179 28.7342 13.3617 28.6282C16.4281 27.8961 20.0901 27.4783 24 27.4783C27.9099 27.4783 31.5719 27.8961 34.6383 28.6282C35.082 28.7342 35.5339 28.8609 35.9868 29.004Z" fill="currentColor"></path>
                            </svg>
                        </div>
                        <h2 class="text-white text-lg font-bold leading-tight tracking-[-0.015em]">Ration Management System</h2>
                    </div>
                    <div class="flex gap-2">
                    
                        
                    </div>
                    <div class="flex flex-1 justify-end gap-8">
                        <div class="flex items-center gap-9">
                            <a class="text-white text-sm font-medium leading-normal cursor-pointer" onclick="showPage('page2')">Dashboard</a>
                            <a class="text-white text-sm font-medium leading-normal" href="#">Products</a>
                            
                        </div>
                        <div class="flex gap-2">
                            <button onclick="showPage('page2')" class="flex min-w-[84px] cursor-pointer items-center justify-center overflow-hidden rounded-full h-10 px-4 bg-[#2d372a] text-white text-sm font-bold leading-normal tracking-[0.015em]">
                                <span class="truncate">Back</span>
                            </button>
                            <button onclick="showPage('page1')" class="flex min-w-[84px] cursor-pointer items-center justify-center overflow-hidden rounded-full h-10 px-4 bg-[#53d22c] text-[#131712] text-sm font-bold leading-normal tracking-[0.015em]">
                                <span class="truncate">Home</span>
                            </button>
                        </div>
                        <div class="bg-center bg-no-repeat aspect-square bg-cover rounded-full size-10" style='background-image: url("https://lh3.googleusercontent.com/aida-public/AB6AXuA60rAEmmJIA_-dNDoiKhHA_ltEm8v0yt1ye60LZixKzI4_uZEFNBq3aE8hmrY3iKmkUL7b2tIgqoU_Kza6mqbkyM8TOWImeXQBHRhlkoMEcv74t_X6TyB7OQzUn_HTE8O-22WaYltIcELCOXqi2wNcK_dF1BEzE2b7xEr6YdyEnI03NJh1_-QANkmsmUVHinXw7y8kqiF8jkssE7gGzV3Fne4gM1yD1w6GlZCetGf0svOvkqMIbSOL5iPyMRGsxasLRlraONFqkxQ");'></div>
                    </div>
                </header>
                <div class="px-40 flex flex-1 justify-center py-5">
                    <div class="layout-content-container flex flex-col max-w-[960px] flex-1">
                        <div class="flex flex-wrap justify-between gap-3 p-4">
                            <p class="text-white tracking-light text-[32px] font-bold leading-tight min-w-72">Shop Inventory Management</p>
                        </div>
                        <h3 class="text-white text-lg font-bold leading-tight tracking-[-0.015em] px-4 pb-2 pt-4">Add New Product</h3>
                        <div class="flex max-w-[480px] flex-wrap items-end gap-4 px-4 py-3">
                            <label class="flex flex-col min-w-40 flex-1">
                                <p class="text-white text-base font-medium leading-normal pb-2">Product Name</p>
                                <input id="newProductName" placeholder="Enter product name" class="form-input flex w-full min-w-0 flex-1 resize-none overflow-hidden rounded-xl text-white focus:outline-0 focus:ring-0 border border-[#42513e] bg-[#1f251d] focus:border-[#42513e] h-14 placeholder:text-[#a5b6a0] p-[15px] text-base font-normal leading-normal" value="" />
                            </label>
                        </div>
                        <div class="flex max-w-[480px] flex-wrap items-end gap-4 px-4 py-3">
                            <label class="flex flex-col min-w-40 flex-1">
                                <p class="text-white text-base font-medium leading-normal pb-2">Quantity (kg)</p>
                                <input id="newProductQuantity" placeholder="Enter quantity in kg" class="form-input flex w-full min-w-0 flex-1 resize-none overflow-hidden rounded-xl text-white focus:outline-0 focus:ring-0 border border-[#42513e] bg-[#1f251d] focus:border-[#42513e] h-14 placeholder:text-[#a5b6a0] p-[15px] text-base font-normal leading-normal" value="" />
                            </label>
                        </div>
                        <div class="flex px-4 py-3 justify-start">
                            <button id="addProduct" class="flex min-w-[84px] max-w-[480px] cursor-pointer items-center justify-center overflow-hidden rounded-full h-10 px-4 bg-[#53d22c] text-[#131712] text-sm font-bold leading-normal tracking-[0.015em]">
                                <span class="truncate">Add Product</span>
                            </button>
                        </div>
                        <h3 class="text-white text-lg font-bold leading-tight tracking-[-0.015em] px-4 pb-2 pt-4">Update Existing Products</h3>
                        <div class="px-4 py-3 @container">
                            <div class="flex overflow-hidden rounded-xl border border-[#42513e] bg-[#131712]">
                                <table class="flex-1">
                                    <thead>
                                        <tr class="bg-[#1f251d]">
                                            <th class="px-4 py-3 text-left text-white w-[150px] text-sm font-medium leading-normal">Actions</th>
                                        </tr>
                                    </thead>
                                    <tbody id="productTableBody">
                                        <tr class="border-t border-t-[#42513e]" data-product="Wheat">
                                            <td class="h-[72px] px-4 py-2 w-[300px] text-white text-sm font-normal leading-normal">Wheat</td>
                                            <td class="h-[72px] px-4 py-2 w-[200px] text-[#a5b6a0] text-sm font-normal leading-normal stock-value">50</td>
                                            <td class="h-[72px] px-4 py-2 w-[200px]">
                                                <input type="number" class="update-input w-20 px-2 py-1 rounded bg-[#1f251d] text-white border border-[#42513e] text-sm" placeholder="Qty" min="0">
                                            </td>
                                            <td class="h-[72px] px-4 py-2 w-[150px]">
                                                <div class="flex gap-2">
                                                    <button class="update-btn px-3 py-1 bg-[#53d22c] text-[#131712] rounded text-sm font-bold hover:bg-[#45b82a] transition-colors">Update</button>
                                                    <button class="delete-btn px-3 py-1 rounded text-sm font-bold">Delete</button>
                                                </div>
                                            </td>
                                        </tr>
                                        <tr class="border-t border-t-[#42513e]" data-product="Rice">
                                            <td class="h-[72px] px-4 py-2 w-[300px] text-white text-sm font-normal leading-normal">Rice</td>
                                            <td class="h-[72px] px-4 py-2 w-[200px] text-[#a5b6a0] text-sm font-normal leading-normal stock-value">100</td>
                                            <td class="h-[72px] px-4 py-2 w-[200px]">
                                                <input type="number" class="update-input w-20 px-2 py-1 rounded bg-[#1f251d] text-white border border-[#42513e] text-sm" placeholder="Qty" min="0">
                                            </td>
                                            <td class="h-[72px] px-4 py-2 w-[150px]">
                                                <div class="flex gap-2">
                                                    <button class="update-btn px-3 py-1 bg-[#53d22c] text-[#131712] rounded text-sm font-bold hover:bg-[#45b82a] transition-colors">Update</button>
                                                    <button class="delete-btn px-3 py-1 rounded text-sm font-bold">Delete</button>
                                                </div>
                                            </td>
                                        </tr>
                                        <tr class="border-t border-t-[#42513e]" data-product="Sugar">
                                            <td class="h-[72px] px-4 py-2 w-[300px] text-white text-sm font-normal leading-normal">Sugar</td>
                                            <td class="h-[72px] px-4 py-2 w-[200px] text-[#a5b6a0] text-sm font-normal leading-normal stock-value">75</td>
                                            <td class="h-[72px] px-4 py-2 w-[200px]">
                                                <input type="number" class="update-input w-20 px-2 py-1 rounded bg-[#1f251d] text-white border border-[#42513e] text-sm" placeholder="Qty" min="0">
                                            </td>
                                            <td class="h-[72px] px-4 py-2 w-[150px]">
                                                <div class="flex gap-2">
                                                    <button class="update-btn px-3 py-1 bg-[#53d22c] text-[#131712] rounded text-sm font-bold hover:bg-[#45b82a] transition-colors">Update</button>
                                                    <button class="delete-btn px-3 py-1 rounded text-sm font-bold">Delete</button>
                                                </div>
                                            </td>
                                        </tr>
                                        <tr class="border-t border-t-[#42513e]" data-product="Lentils">
                                            <td class="h-[72px] px-4 py-2 w-[300px] text-white text-sm font-normal leading-normal">Lentils</td>
                                            <td class="h-[72px] px-4 py-2 w-[200px] text-[#a5b6a0] text-sm font-normal leading-normal stock-value">60</td>
                                            <td class="h-[72px] px-4 py-2 w-[200px]">
                                                <input type="number" class="update-input w-20 px-2 py-1 rounded bg-[#1f251d] text-white border border-[#42513e] text-sm" placeholder="Qty" min="0">
                                            </td>
                                            <td class="h-[72px] px-4 py-2 w-[150px]">
                                                <div class="flex gap-2">
                                                    <button class="update-btn px-3 py-1 bg-[#53d22c] text-[#131712] rounded text-sm font-bold hover:bg-[#45b82a] transition-colors">Update</button>
                                                    <button class="delete-btn px-3 py-1 rounded text-sm font-bold">Delete</button>
                                                </div>
                                            </td>
                                        </tr>
                                        <tr class="border-t border-t-[#42513e]" data-product="Cooking Oil">
                                            <td class="h-[72px] px-4 py-2 w-[300px] text-white text-sm font-normal leading-normal">Cooking Oil</td>
                                            <td class="h-[72px] px-4 py-2 w-[200px] text-[#a5b6a0] text-sm font-normal leading-normal stock-value">40</td>
                                            <td class="h-[72px] px-4 py-2 w-[200px]">
                                                <input type="number" class="update-input w-20 px-2 py-1 rounded bg-[#1f251d] text-white border border-[#42513e] text-sm" placeholder="Qty" min="0">
                                            </td>
                                            <td class="h-[72px] px-4 py-2 w-[150px]">
                                                <div class="flex gap-2">
                                                    <button class="update-btn px-3 py-1 bg-[#53d22c] text-[#131712] rounded text-sm font-bold hover:bg-[#45b82a] transition-colors">Update</button>
                                                    <button class="delete-btn px-3 py-1 rounded text-sm font-bold">Delete</button>
                                                </div>
                                            </td>
                                        </tr>
                                    </tbody>
                                </table>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Delete Confirmation Modal -->
        <div id="deleteConfirmModal" class="fixed inset-0 confirm-modal flex items-center justify-center z-50" style="display: none;">
            <div class="bg-[#1f251d] p-8 rounded-xl border border-[#42513e] max-w-md w-full mx-4">
                <h3 class="text-white text-xl font-bold mb-4">Confirm Deletion</h3>
                <p class="text-[#a5b6a0] mb-6">Are you sure you want to delete <strong id="deleteProductName" class="text-white"></strong>? This action cannot be undone.</p>
                <div class="flex gap-3">
                    <button id="confirmDeleteBtn" class="flex-1 cursor-pointer items-center justify-center overflow-hidden rounded-full h-10 px-4 bg-[#ef4444] text-white text-sm font-bold leading-normal tracking-[0.015em] hover:bg-[#dc2626] transition-colors">
                        Delete
                    </button>
                    <button id="cancelDeleteBtn" class="flex-1 cursor-pointer items-center justify-center overflow-hidden rounded-full h-10 px-4 bg-[#2d372a] text-white text-sm font-bold leading-normal tracking-[0.015em]">
                        Cancel
                    </button>
                </div>
            </div>
        </div>

        <!-- Page 4: User Login -->
        <div id="page4" class="page">
            <div class="layout-container flex h-full grow flex-col">
                <header class="flex items-center justify-between whitespace-nowrap border-b border-solid border-b-[#2d372a] px-10 py-3">
                    <div class="flex items-center gap-4 text-white">
                        <div class="size-4">
                            <svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path d="M13.8261 30.5736C16.7203 29.8826 20.2244 29.4783 24 29.4783C27.7756 29.4783 31.2797 29.8826 34.1739 30.5736C36.9144 31.2278 39.9967 32.7669 41.3563 33.8352L24.8486 7.36089C24.4571 6.73303 23.5429 6.73303 23.1514 7.36089L6.64374 33.8352C8.00331 32.7669 11.0856 31.2278 13.8261 30.5736Z" fill="currentColor"></path>
                                <path fill-rule="evenodd" clip-rule="evenodd" d="M39.998 35.764C39.9944 35.7463 39.9875 35.7155 39.9748 35.6706C39.9436 35.5601 39.8949 35.4259 39.8346 35.2825C39.8168 35.2403 39.7989 35.1993 39.7813 35.1602C38.5103 34.2887 35.9788 33.0607 33.7095 32.5189C30.9875 31.8691 27.6413 31.4783 24 31.4783C20.3587 31.4783 17.0125 31.8691 14.2905 32.5189C12.0012 33.0654 9.44505 34.3104 8.18538 35.1832C8.17384 35.2075 8.16216 35.233 8.15052 35.2592C8.09919 35.3751 8.05721 35.4886 8.02977 35.589C8.00356 35.6848 8.00039 35.7333 8.00004 35.7388C8.00004 35.739 8 35.7393 8.00004 35.7388C8.00004 35.7641 8.0104 36.0767 8.68485 36.6314C9.34546 37.1746 10.4222 37.7531 11.9291 38.2772C14.9242 39.319 19.1919 40 24 40C28.8081 40 33.0758 39.319 36.0709 38.2772C37.5778 37.7531 38.6545 37.1746 39.3151 36.6314C39.9006 36.1499 39.9857 35.8511 39.998 35.764ZM4.95178 32.7688L21.4543 6.30267C22.6288 4.4191 25.3712 4.41909 26.5457 6.30267L43.0534 32.777C43.0709 32.8052 43.0878 32.8338 43.104 32.8629L41.3563 33.8352C43.104 32.8629 43.1038 32.8626 43.104 32.8629L43.1051 32.865L43.1065 32.8675L43.1101 32.8739L43.1199 32.8918C43.1276 32.906 43.1377 32.9246 43.1497 32.9473C43.1738 32.9925 43.2062 33.0545 43.244 33.1299C43.319 33.2792 43.4196 33.489 43.5217 33.7317C43.6901 34.1321 44 34.9311 44 35.7391C44 37.4427 43.003 38.7775 41.8558 39.7209C40.6947 40.6757 39.1354 41.4464 37.385 42.0552C33.8654 43.2794 29.133 44 24 44C18.867 44 14.1346 43.2794 10.615 42.0552C8.86463 41.4464 7.30529 40.6757 6.14419 39.7209C4.99695 38.7775 3.99999 37.4427 3.99999 35.7391C3.99999 34.8725 4.29264 34.0922 4.49321 33.6393C4.60375 33.3898 4.71348 33.1804 4.79687 33.0311C4.83898 32.9556 4.87547 32.8935 4.9035 32.8471C4.91754 32.8238 4.92954 32.8043 4.93916 32.7889L4.94662 32.777L4.95178 32.7688ZM35.9868 29.004L24 9.77997L12.0131 29.004C12.4661 28.8609 12.9179 28.7342 13.3617 28.6282C16.4281 27.8961 20.0901 27.4783 24 27.4783C27.9099 27.4783 31.5719 27.8961 34.6383 28.6282C35.082 28.7342 35.5339 28.8609 35.9868 29.004Z" fill="currentColor"></path>
                            </svg>
                        </div>
                        <h2 class="text-white text-lg font-bold leading-tight tracking-[-0.015em]">Ration Management System</h2>
                    </div>
                </header>
                <div class="px-40 flex flex-1 justify-center py-5">
                    <div class="layout-content-container flex flex-col w-[512px] max-w-[512px] py-5 max-w-[960px] flex-1">
                        <h2 class="text-white tracking-light text-[28px] font-bold leading-tight px-4 text-center pb-3 pt-5">Login as User</h2>
                        <div class="flex max-w-[480px] flex-wrap items-end gap-4 px-4 py-3">
                            <label class="flex flex-col min-w-40 flex-1">
                                <input id="phoneNumber" placeholder="Enter your phone number" class="form-input flex w-full min-w-0 flex-1 resize-none overflow-hidden rounded-xl text-white focus:outline-0 focus:ring-0 border border-[#42513e] bg-[#1f251d] focus:border-[#42513e] h-14 placeholder:text-[#a5b6a0] p-[15px] text-base font-normal leading-normal" value="" />
                            </label>
                        </div>
                        <div class="flex px-4 py-3 justify-center">
                            <button id="sendOtp" class="flex min-w-[84px] max-w-[480px] cursor-pointer items-center justify-center overflow-hidden rounded-full h-10 px-4 bg-[#53d22c] text-[#131712] text-sm font-bold leading-normal tracking-[0.015em]">
                                <span class="truncate">Send OTP</span>
                            </button>
                        </div>
                        <div class="flex max-w-[480px] flex-wrap items-end gap-4 px-4 py-3">
                            <label class="flex flex-col min-w-40 flex-1">
                                <input id="otpInput" placeholder="Enter OTP" class="form-input flex w-full min-w-0 flex-1 resize-none overflow-hidden rounded-xl text-white focus:outline-0 focus:ring-0 border border-[#42513e] bg-[#1f251d] focus:border-[#42513e] h-14 placeholder:text-[#a5b6a0] p-[15px] text-base font-normal leading-normal" value="" disabled />
                            </label>
                        </div>
                        <div class="flex px-4 py-3 justify-center">
                            <button id="verifyOtp" class="flex min-w-[84px] max-w-[480px] cursor-pointer items-center justify-center overflow-hidden rounded-full h-10 px-4 bg-[#2d372a] text-white text-sm font-bold leading-normal tracking-[0.015em] opacity-50 cursor-not-allowed" disabled>
                                <span class="truncate">Verify OTP</span>
                            </button>
                        </div>
                        <div class="flex px-4 py-3 justify-center">
                            <button id="backToHome" class="flex min-w-[84px] max-w-[480px] cursor-pointer items-center justify-center overflow-hidden rounded-full h-10 px-4 bg-[#2d372a] text-white text-sm font-bold leading-normal tracking-[0.015em]">
                                <span class="truncate">Back to Home</span>
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Page 5: User Inventory View -->
        <div id="page5" class="page">
            <div class="layout-container flex h-full grow flex-col">
                <header class="flex items-center justify-between whitespace-nowrap border-b border-solid border-b-[#2d372a] px-10 py-3">
                    <div class="flex items-center gap-4 text-white">
                        <div class="size-4">
                            <svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path d="M24 45.8096C19.6865 45.8096 15.4698 44.5305 11.8832 42.134C8.29667 39.7376 5.50128 36.3314 3.85056 32.3462C2.19985 28.361 1.76794 23.9758 2.60947 19.7452C3.451 15.5145 5.52816 11.6284 8.57829 8.5783C11.6284 5.52817 15.5145 3.45101 19.7452 2.60948C23.9758 1.76795 28.361 2.19986 32.3462 3.85057C36.3314 5.50129 39.7376 8.29668 42.134 11.8833C44.5305 15.4698 45.8096 19.6865 45.8096 24L24 24L24 45.8096Z" fill="currentColor"></path>
                            </svg>
                        </div>
                        <h2 class="text-white text-lg font-bold leading-tight tracking-[-0.015em]">Ration System</h2>
                    </div>
                    <div class="flex flex-1 justify-end gap-8">
                        <div class="flex items-center gap-9">
                            <a class="text-white text-sm font-medium leading-normal cursor-pointer" onclick="showPage('page1')">Home</a>
                            <a class="text-white text-sm font-medium leading-normal" href="#">Inventory</a>
                            
                        </div>
                        <div class="flex gap-2">
                            <button onclick="showPage('page4')" class="flex min-w-[84px] cursor-pointer items-center justify-center overflow-hidden rounded-full h-10 px-4 bg-[#2d372a] text-white text-sm font-bold leading-normal tracking-[0.015em]">
                                <span class="truncate">Back</span>
                            </button>
                            <button onclick="showPage('page1')" class="flex min-w-[84px] cursor-pointer items-center justify-center overflow-hidden rounded-full h-10 px-4 bg-[#53d22c] text-[#131712] text-sm font-bold leading-normal tracking-[0.015em]">
                                <span class="truncate">Home</span>
                            </button>
                        </div>
                        <button class="flex max-w-[480px] cursor-pointer items-center justify-center overflow-hidden rounded-full h-10 bg-[#2d372a] text-white gap-2 text-sm font-bold leading-normal tracking-[0.015em] min-w-0 px-2.5">
                            <div class="text-white" data-icon="Bell" data-size="20px" data-weight="regular">
                                <svg xmlns="http://www.w3.org/2000/svg" width="20px" height="20px" fill="currentColor" viewBox="0 0 256 256">
                                    <path d="M221.8,175.94C216.25,166.38,208,139.33,208,104a80,80,0,1,0-160,0c0,35.34-8.26,62.38-13.81,71.94A16,16,0,0,0,48,200H88.81a40,40,0,0,0,78.38,0H208a16,16,0,0,0,13.8-24.06ZM128,216a24,24,0,0,1-22.62-16h45.24A24,24,0,0,1,128,216ZM48,184c7.7-13.24,16-43.92,16-80a64,64,0,1,1,128,0c0,36.05,8.28,66.73,16,80Z"></path>
                                </svg>
                            </div>
                        </button>
                        <div class="bg-center bg-no-repeat aspect-square bg-cover rounded-full size-10" style='background-image: url("https://lh3.googleusercontent.com/aida-public/AB6AXuACyH87JhoERRshBRArMP6zoyWfZh-e8chFRUQ-sFLcINeoeBXlgQj8Vye0jEOHip-CkDlnKFm1g8gXKPxDoIFdoQcOyr_9YCeZ7oeyU34RSzBZ-BPjfjvW505zZJYVhl9lYlLmgM3-SHwUkrRiRkwOozZgA3bZPkkkqb_eKi3FiFiBwxKWZAYM5Y7k8Yi1Q01DZO04qMGF-UOiVctnCp3R6g412MjmAXLrCY4ODu1T-jSNdWyEsMGG13VGk9P_ZRmmey9yqBMVUWw");'></div>
                    </div>
                </header>
                <div class="px-40 flex flex-1 justify-center py-5">
                    <div class="layout-content-container flex flex-col max-w-[960px] flex-1">
                        <div class="flex flex-wrap justify-between gap-3 p-4">
                            <p class="text-white tracking-light text-[32px] font-bold leading-tight min-w-72">Inventory</p>
                        </div>
                        <div class="px-4 py-3 @container">
                            <div class="flex overflow-hidden rounded-xl border border-[#42513e] bg-[#131712]">
                                <table class="flex-1">
                                    <thead>
                                        <tr class="bg-[#1f251d]">
                                            <th class="px-4 py-3 text-left text-white w-[400px] text-sm font-medium leading-normal">Product Name</th>
                                            <th class="px-4 py-3 text-left text-white w-[400px] text-sm font-medium leading-normal">Availability</th>
                                        </tr>
                                    </thead>
                                    <tbody id="userInventoryTable">
                                        <tr class="border-t border-t-[#42513e]">
                                            <td class="h-[72px] px-4 py-2 w-[400px] text-white text-sm font-normal leading-normal">Wheat</td>
                                            <td class="h-[72px] px-4 py-2 w-[400px] text-[#a5b6a0] text-sm font-normal leading-normal availability-value">100 kg</td>
                                        </tr>
                                        <tr class="border-t border-t-[#42513e]">
                                            <td class="h-[72px] px-4 py-2 w-[400px] text-white text-sm font-normal leading-normal">Rice</td>
                                            <td class="h-[72px] px-4 py-2 w-[400px] text-[#a5b6a0] text-sm font-normal leading-normal availability-value">150 kg</td>
                                        </tr>
                                        <tr class="border-t border-t-[#42513e]">
                                            <td class="h-[72px] px-4 py-2 w-[400px] text-white text-sm font-normal leading-normal">Sugar</td>
                                            <td class="h-[72px] px-4 py-2 w-[400px] text-[#a5b6a0] text-sm font-normal leading-normal availability-value">75 kg</td>
                                        </tr>
                                        <tr class="border-t border-t-[#42513e]">
                                            <td class="h-[72px] px-4 py-2 w-[400px] text-white text-sm font-normal leading-normal">Lentils</td>
                                            <td class="h-[72px] px-4 py-2 w-[400px] text-[#a5b6a0] text-sm font-normal leading-normal availability-value">50 kg</td>
                                        </tr>
                                        <tr class="border-t border-t-[#42513e]">
                                            <td class="h-[72px] px-4 py-2 w-[400px] text-white text-sm font-normal leading-normal">Cooking Oil</td>
                                            <td class="h-[72px] px-4 py-2 w-[400px] text-[#a5b6a0] text-sm font-normal leading-normal availability-value">20 liters</td>
                                        </tr>
                                    </tbody>
                                </table>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Notification Container -->
        <div id="notification" class="notification"></div>
    </div>

    <script>
        // Global variables
        let currentPage = 'page1';
        let otpSent = false;
        let generatedOtp = '';
        let productToDelete = null;
        
        // Inventory data synchronization
        const inventoryData = {
            'Wheat': 50,
            'Rice': 100,
            'Sugar': 75,
            'Lentils': 60,
            'Cooking Oil': 40
        };

        // Show notification function
        function showNotification(message, type = 'success') {
            const notification = document.getElementById('notification');
            notification.textContent = message;
            
            // Remove existing type classes
            notification.classList.remove('bg-red-500', 'bg-green-500', 'bg-blue-500');
            
            // Add appropriate background color based on type
            switch(type) {
                case 'error':
                    notification.style.background = '#ef4444';
                    notification.style.color = 'white';
                    break;
                case 'warning':
                    notification.style.background = '#f59e0b';
                    notification.style.color = 'white';
                    break;
                case 'info':
                    notification.style.background = '#3b82f6';
                    notification.style.color = 'white';
                    break;
                default: // success
                    notification.style.background = '#53d22c';
                    notification.style.color = '#131712';
            }
            
            notification.classList.add('show');
            
            setTimeout(() => {
                notification.classList.remove('show');
            }, 3000);
        }

        // Show page function
        function showPage(pageId) {
            // Hide all pages
            document.querySelectorAll('.page').forEach(page => {
                page.classList.remove('active');
            });
            
            // Show selected page
            document.getElementById(pageId).classList.add('active');
            document.getElementById(pageId).classList.add('fade-in');
            
            currentPage = pageId;
            
            // Remove fade-in class after animation
            setTimeout(() => {
                document.getElementById(pageId).classList.remove('fade-in');
            }, 300);
        }

        // Delete product function
        function deleteProduct(productName) {
            // Remove from inventory data
            delete inventoryData[productName];
            
            // Remove from shop management table
            const row = document.querySelector(`tr[data-product="${productName}"]`);
            if (row) {
                row.remove();
            }
            
            // Update user inventory view
            updateUserInventory();
            
            showNotification(`${productName} deleted successfully!`, 'info');
        }

        // Show delete confirmation modal
        function showDeleteConfirmation(productName) {
            productToDelete = productName;
            document.getElementById('deleteProductName').textContent = productName;
            document.getElementById('deleteConfirmModal').style.display = 'flex';
        }

        // Hide delete confirmation modal
        function hideDeleteConfirmation() {
            productToDelete = null;
            document.getElementById('deleteConfirmModal').style.display = 'none';
        }

        // Initialize event listeners
        document.addEventListener('DOMContentLoaded', function() {
            // Page 1 - Login buttons
            document.getElementById('loginUser').addEventListener('click', function() {
                showPage('page4');
            });
            
            document.getElementById('loginShopOwner').addEventListener('click', function() {
                showPage('page2');
            });

            // Page 2 - Shop selection
            document.querySelectorAll('.shop-item').forEach(item => {
                item.addEventListener('click', function() {
                    document.getElementById('passwordModal').style.display = 'flex';
                });
            });

            document.getElementById('cancelPassword').addEventListener('click', function() {
                document.getElementById('passwordModal').style.display = 'none';
                document.getElementById('shopPassword').value = '';
            });

            document.getElementById('verifyPassword').addEventListener('click', function() {
                const password = document.getElementById('shopPassword').value;
                if (password === 'admin123' || password === 'shop123') {
                    document.getElementById('passwordModal').style.display = 'none';
                    document.getElementById('shopPassword').value = '';
                    showNotification('Login successful!');
                    showPage('page3');
                } else {
                    showNotification('Invalid password!', 'error');
                }
            });

            // Delete confirmation modal event listeners
            document.getElementById('confirmDeleteBtn').addEventListener('click', function() {
                if (productToDelete) {
                    deleteProduct(productToDelete);
                    hideDeleteConfirmation();
                }
            });

            document.getElementById('cancelDeleteBtn').addEventListener('click', function() {
                hideDeleteConfirmation();
            });

            // Page 3 - Inventory management
            document.getElementById('addProduct').addEventListener('click', function() {
                const productName = document.getElementById('newProductName').value.trim();
                const quantity = document.getElementById('newProductQuantity').value.trim();
                
                if (productName && quantity && !isNaN(quantity) && quantity >= 0) {
                    if (inventoryData.hasOwnProperty(productName)) {
                        showNotification('Product already exists! Use update instead.', 'warning');
                        return;
                    }
                    
                    // Add to inventory data
                    inventoryData[productName] = parseInt(quantity);
                    
                    // Add to table
                    const tbody = document.getElementById('productTableBody');
                    const newRow = document.createElement('tr');
                    newRow.className = 'border-t border-t-[#42513e]';
                    newRow.setAttribute('data-product', productName);
                    newRow.innerHTML = `
                        <td class="h-[72px] px-4 py-2 w-[300px] text-white text-sm font-normal leading-normal">${productName}</td>
                        <td class="h-[72px] px-4 py-2 w-[200px] text-[#a5b6a0] text-sm font-normal leading-normal stock-value">${quantity}</td>
                        <td class="h-[72px] px-4 py-2 w-[200px]">
                            <input type="number" class="update-input w-20 px-2 py-1 rounded bg-[#1f251d] text-white border border-[#42513e] text-sm" placeholder="Qty" min="0">
                        </td>
                        <td class="h-[72px] px-4 py-2 w-[150px]">
                            <div class="flex gap-2">
                                <button class="update-btn px-3 py-1 bg-[#53d22c] text-[#131712] rounded text-sm font-bold hover:bg-[#45b82a] transition-colors">Update</button>
                                <button class="delete-btn px-3 py-1 rounded text-sm font-bold">Delete</button>
                            </div>
                        </td>
                    `;
                    tbody.appendChild(newRow);
                    
                    // Clear inputs
                    document.getElementById('newProductName').value = '';
                    document.getElementById('newProductQuantity').value = '';
                    
                    // Update user inventory view
                    updateUserInventory();
                    
                    showNotification(`${productName} added successfully!`);
                } else {
                    showNotification('Please enter valid product name and quantity!', 'error');
                }
            });

            // Update stock and delete buttons - Enhanced functionality
            document.addEventListener('click', function(e) {
                if (e.target.classList.contains('update-btn')) {
                    const row = e.target.closest('tr');
                    const productName = row.getAttribute('data-product');
                    const input = row.querySelector('.update-input');
                    const newQuantity = input.value.trim();
                    
                    if (newQuantity && !isNaN(newQuantity) && newQuantity >= 0) {
                        const quantityNum = parseInt(newQuantity);
                        
                        // Update inventory data
                        inventoryData[productName] = quantityNum;
                        
                        // Update display in shop management table
                        row.querySelector('.stock-value').textContent = quantityNum;
                        input.value = '';
                        
                        // Update user inventory view
                        updateUserInventory();
                        
                        // Show success notification
                        showNotification(`${productName} stock updated to ${quantityNum} ${productName === 'Cooking Oil' ? 'liters' : 'kg'}!`);
                    } else {
                        showNotification('Please enter a valid quantity (0 or greater)!', 'error');
                        input.focus();
                    }
                } else if (e.target.classList.contains('delete-btn')) {
                    const row = e.target.closest('tr');
                    const productName = row.getAttribute('data-product');
                    showDeleteConfirmation(productName);
                }
            });

            // Add Enter key support for update inputs
            document.addEventListener('keypress', function(e) {
                if (e.key === 'Enter' && e.target.classList.contains('update-input')) {
                    const updateBtn = e.target.parentElement.parentElement.querySelector('.update-btn');
                    if (updateBtn) {
                        updateBtn.click();
                    }
                }
            });

            // Page 4 - User login
            document.getElementById('sendOtp').addEventListener('click', function() {
                const phoneNumber = document.getElementById('phoneNumber').value.trim();
                if (phoneNumber && phoneNumber.length === 10 && /^\d+$/.test(phoneNumber)) {
                    // Generate random OTP
                    generatedOtp = Math.floor(1000 + Math.random() * 9000).toString();
                    otpSent = true;
                    
                    // Enable OTP input and verify button
                    document.getElementById('otpInput').disabled = false;
                    document.getElementById('verifyOtp').disabled = false;
                    document.getElementById('verifyOtp').classList.remove('opacity-50', 'cursor-not-allowed');
                    document.getElementById('verifyOtp').classList.add('bg-[#53d22c]', 'text-[#131712]');
                    
                    showNotification(`OTP sent to ${phoneNumber}! OTP: ${generatedOtp}`);
                } else {
                    showNotification('Please enter a valid 10-digit phone number!', 'error');
                }
            });

            document.getElementById('verifyOtp').addEventListener('click', function() {
                const enteredOtp = document.getElementById('otpInput').value.trim();
                if (otpSent && enteredOtp === generatedOtp) {
                    showNotification('OTP verified successfully!');
                    showPage('page5');
                    // Reset OTP state
                    otpSent = false;
                    generatedOtp = '';
                    document.getElementById('phoneNumber').value = '';
                    document.getElementById('otpInput').value = '';
                    document.getElementById('otpInput').disabled = true;
                    document.getElementById('verifyOtp').disabled = true;
                    document.getElementById('verifyOtp').classList.add('opacity-50', 'cursor-not-allowed');
                    document.getElementById('verifyOtp').classList.remove('bg-[#53d22c]', 'text-[#131712]');
                } else {
                    showNotification('Invalid OTP! Please try again.', 'error');
                }
            });

            document.getElementById('backToHome').addEventListener('click', function() {
                showPage('page1');
                // Reset form
                document.getElementById('phoneNumber').value = '';
                document.getElementById('otpInput').value = '';
                document.getElementById('otpInput').disabled = true;
                document.getElementById('verifyOtp').disabled = true;
                document.getElementById('verifyOtp').classList.add('opacity-50', 'cursor-not-allowed');
                document.getElementById('verifyOtp').classList.remove('bg-[#53d22c]', 'text-[#131712]');
                otpSent = false;
                generatedOtp = '';
            });

            // Initialize user inventory view
            updateUserInventory();
        });

        // Function to update user inventory view
        function updateUserInventory() {
            const userTable = document.getElementById('userInventoryTable');
            userTable.innerHTML = '';
            
            for (const [product, quantity] of Object.entries(inventoryData)) {
                const row = document.createElement('tr');
                row.className = 'border-t border-t-[#42513e]';
                
                let displayQuantity = quantity;
                if (product === 'Cooking Oil') {
                    displayQuantity = quantity + ' liters';
                } else {
                    displayQuantity = quantity + ' kg';
                }
                
                row.innerHTML = `
                    <td class="h-[72px] px-4 py-2 w-[400px] text-white text-sm font-normal leading-normal">${product}</td>
                    <td class="h-[72px] px-4 py-2 w-[400px] text-[#a5b6a0] text-sm font-normal leading-normal availability-value">${displayQuantity}</td>
                `;
                userTable.appendChild(row);
            }
        }

        // Handle Enter key for password input and other modals
        document.addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                if (document.getElementById('passwordModal').style.display === 'flex') {
                    document.getElementById('verifyPassword').click();
                } else if (document.getElementById('deleteConfirmModal').style.display === 'flex') {
                    document.getElementById('confirmDeleteBtn').click();
                } else if (currentPage === 'page4') {
                    const phoneInput = document.getElementById('phoneNumber');
                    const otpInput = document.getElementById('otpInput');
                    
                    if (document.activeElement === phoneInput && !otpSent) {
                        document.getElementById('sendOtp').click();
                    } else if (document.activeElement === otpInput && otpSent) {
                        document.getElementById('verifyOtp').click();
                    }
                }
            }
        });

        // Close modals when clicking outside
        document.getElementById('passwordModal').addEventListener('click', function(e) {
            if (e.target === this) {
                this.style.display = 'none';
                document.getElementById('shopPassword').value = '';
            }
        });

        document.getElementById('deleteConfirmModal').addEventListener('click', function(e) {
            if (e.target === this) {
                hideDeleteConfirmation();
            }
        });

        // Handle ESC key to close modals
        document.addEventListener('keydown', function(e) {
            if (e.key === 'Escape') {
                if (document.getElementById('passwordModal').style.display === 'flex') {
                    document.getElementById('passwordModal').style.display = 'none';
                    document.getElementById('shopPassword').value = '';
                } else if (document.getElementById('deleteConfirmModal').style.display === 'flex') {
                    hideDeleteConfirmation();
                }
            }
        });

        // Add input validation for phone number
        document.getElementById('phoneNumber').addEventListener('input', function(e) {
            let value = e.target.value.replace(/\D/g, ''); // Remove non-digits
            if (value.length > 10) {
                value = value.slice(0, 10); // Limit to 10 digits
            }
            e.target.value = value;
        });

        // Add input validation for OTP
        document.getElementById('otpInput').addEventListener('input', function(e) {
            let value = e.target.value.replace(/\D/g, ''); // Remove non-digits
            if (value.length > 4) {
                value = value.slice(0, 4); // Limit to 4 digits
            }
            e.target.value = value;
        });

        // Add input validation for product quantity
        document.getElementById('newProductQuantity').addEventListener('input', function(e) {
            let value = e.target.value.replace(/[^\d.]/g, ''); // Only allow digits and decimal
            e.target.value = value;
        });

        // Add hover effects for shop items
        document.querySelectorAll('.shop-item').forEach(item => {
            item.addEventListener('mouseenter', function() {
                this.style.transform = 'translateY(-2px)';
                this.style.transition = 'transform 0.2s ease';
            });
            
            item.addEventListener('mouseleave', function() {
                this.style.transform = 'translateY(0)';
            });
        });

        // Auto-save functionality for shop data
        function saveShopData() {
            try {
                const shopData = {
                    inventory: inventoryData,
                    lastUpdated: new Date().toISOString()
                };
                // In a real application, this would be saved to a server
                console.log('Shop data saved:', shopData);
            } catch (error) {
                console.error('Error saving shop data:', error);
            }
        }

        // Save data whenever inventory is updated
        document.addEventListener('click', function(e) {
            if (e.target.classList.contains('update-btn') || e.target.id === 'addProduct' || e.target.classList.contains('delete-btn')) {
                setTimeout(saveShopData, 100); // Save after DOM updates
            }
        });

        // Data validation for product updates
        function validateProductData(name, quantity) {
            if (!name || name.trim().length === 0) {
                return { valid: false, message: 'Product name cannot be empty' };
            }
            
            if (!quantity || isNaN(quantity) || quantity < 0) {
                return { valid: false, message: 'Quantity must be a valid positive number' };
            }
            
            if (quantity > 10000) {
                return { valid: false, message: 'Quantity cannot exceed 10,000 kg' };
            }
            
            return { valid: true };
        }

        // Add keyboard shortcuts
        document.addEventListener('keydown', function(e) {
            // Alt + H for Home
            if (e.altKey && e.key === 'h') {
                e.preventDefault();
                showPage('page1');
                showNotification('Navigated to Home', 'info');
            }
            
            // Alt + L for Logout (go to home)
            if (e.altKey && e.key === 'l') {
                e.preventDefault();
                showPage('page1');
                showNotification('Logged out successfully', 'info');
            }
        });

        // Enhanced styling
        const style = document.createElement('style');
        style.textContent = `
            .page {
                opacity: 0;
                transition: opacity 0.3s ease-in-out;
            }
            .page.active {
                opacity: 1;
            }
            .notification.error {
                background: #ef4444 !important;
                color: white !important;
            }
            .shop-item:hover {
                transform: translateY(-2px);
                transition: transform 0.2s ease;
            }
            .update-btn:hover {
                transform: scale(1.05);
                transition: transform 0.1s ease;
            }
            .delete-btn:hover {
                transform: scale(1.05);
                transition: transform 0.1s ease;
            }
            .form-input:focus {
                box-shadow: 0 0 0 2px rgba(83, 210, 44, 0.3);
            }
            .confirm-modal {
                animation: fadeIn 0.3s ease;
            }
            @keyframes fadeIn {
                from { opacity: 0; }
                to { opacity: 1; }
            }
        `;
        document.head.appendChild(style);

        // Initialize tooltips for better UX
        function addTooltips() {
            const tooltipElements = [
                { id: 'sendOtp', text: 'Click to receive OTP on your phone' },
                { id: 'verifyOtp', text: 'Enter the 4-digit OTP you received' },
                { id: 'addProduct', text: 'Add a new product to inventory' }
            ];

            tooltipElements.forEach(({ id, text }) => {
                const element = document.getElementById(id);
                if (element) {
                    element.title = text;
                }
            });

            // Add tooltips for delete buttons
            document.querySelectorAll('.delete-btn').forEach(btn => {
                btn.title = 'Delete this product from inventory';
            });

            document.querySelectorAll('.update-btn').forEach(btn => {
                btn.title = 'Update product quantity';
            });
        }

        // Call tooltip initialization
        setTimeout(addTooltips, 100);

        // Prevent form submission on enter
        document.addEventListener('submit', function(e) {
            e.preventDefault();
        });

        console.log('Ration Management System with Delete Feature initialized successfully!');
    </script>
</body>
</html>
