Source PDF: <file:///Users/motyzas/metallRef/MetalRefMaterials/Metal_by_Tutorials_v5.0.0m.pdf>

<a id="page-1"></a>

![Figure](Metal_by_Tutorials_v500mpdf/c6660d9a513fcd70dd1df8d5.png)

<a id="page-2"></a>

## **Metal by Tutorials**

By Caroline Begbie & Marius Horga

Copyright ©2025 Kodeco Inc.

## **Notice of Rights**

All rights reserved. No part of this book or corresponding materials (such as text, images, or source code) may be reproduced or distributed by any means without prior written permission of the copyright owner.

## **Notice of Liability**

This book and all corresponding materials (such as source code) are provided on an “as is” basis, without warranty of any kind, express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose, and noninfringement. In no event shall the authors or copyright holders be liable for any claim, damages or other liability, whether in action of contract, tort or otherwise, arising from, out of or in connection with the software or the use of other dealing in the software.

## **Trademarks**

All trademarks and registered trademarks appearing in this book are the property of their own respective owners.

<a id="page-3"></a>

# Table of Contents: Overview

<table data-pdf-contents="true">
<tr><th>Entry</th><th>Page</th></tr>
<tr data-level="1"><td><strong><a href="#page-16">Book License</a></strong></td><td>16</td></tr>
<tr data-level="1"><td><strong><a href="#page-17">Before You Begin</a></strong></td><td>17</td></tr>
<tr data-level="1"><td><strong><a href="#page-18">What You Need</a></strong></td><td>18</td></tr>
<tr data-level="1"><td><strong><a href="#page-19">Book Source Code &amp; Forums</a></strong></td><td>19</td></tr>
<tr data-level="1"><td><strong><a href="#page-22">Acknowledgments</a></strong></td><td>22</td></tr>
<tr data-level="1"><td><strong><a href="#page-23">Introduction</a></strong></td><td>23</td></tr>
<tr data-level="1"><td><strong><a href="#page-28">Section I: Beginning Metal</a></strong></td><td>28</td></tr>
<tr data-level="1"><td><strong><a href="#page-29">Chapter 1: Hello, Metal!</a></strong></td><td>29</td></tr>
<tr data-level="1"><td><strong><a href="#page-46">Chapter 2: 3D Models</a></strong></td><td>46</td></tr>
<tr data-level="1"><td><strong><a href="#page-73">Chapter 3: The Rendering Pipeline</a></strong></td><td>73</td></tr>
<tr data-level="1"><td><strong><a href="#page-98">Chapter 4: The Vertex Function</a></strong></td><td>98</td></tr>
<tr data-level="1"><td><strong><a href="#page-119">Chapter 5: 3D Transformations</a></strong></td><td>119</td></tr>
<tr data-level="1"><td><strong><a href="#page-134">Chapter 6: Coordinate Spaces</a></strong></td><td>134</td></tr>
<tr data-level="1"><td><strong><a href="#page-155">Chapter 7: The Fragment Function</a></strong></td><td>155</td></tr>
<tr data-level="1"><td><strong><a href="#page-178">Chapter 8: Textures</a></strong></td><td>178</td></tr>
<tr data-level="1"><td><strong><a href="#page-215">Chapter 9: Navigating a 3D Scene</a></strong></td><td>215</td></tr>
<tr data-level="1"><td><strong><a href="#page-244">Chapter 10: Lighting Fundamentals</a></strong></td><td>244</td></tr>
<tr data-level="1"><td><strong><a href="#page-272">Section II: Intermediate Metal</a></strong></td><td>272</td></tr>
<tr data-level="1"><td><strong><a href="#page-273">Chapter 11: Maps &amp; Materials</a></strong></td><td>273</td></tr>
<tr data-level="1"><td><strong><a href="#page-304">Chapter 12: Render Passes</a></strong></td><td>304</td></tr>
<tr data-level="1"><td><strong><a href="#page-326">Chapter 13: Shadows</a></strong></td><td>326</td></tr>
</table>

<a id="page-4"></a>

<table data-pdf-contents="true">
<tr><th>Entry</th><th>Page</th></tr>
<tr data-level="1"><td><strong><a href="#page-349">Chapter 14: Deferred Rendering</a></strong></td><td>349</td></tr>
<tr data-level="1"><td><strong><a href="#page-379">Chapter 15: Tile-Based Deferred Rendering</a></strong></td><td>379</td></tr>
<tr data-level="1"><td><strong><a href="#page-405">Chapter 16: GPU Compute Programming</a></strong></td><td>405</td></tr>
<tr data-level="1"><td><strong><a href="#page-421">Chapter 17: Particle Systems</a></strong></td><td>421</td></tr>
<tr data-level="1"><td><strong><a href="#page-446">Chapter 18: Particle Behavior</a></strong></td><td>446</td></tr>
<tr data-level="1"><td><strong><a href="#page-466">Section III: Advanced Metal</a></strong></td><td>466</td></tr>
<tr data-level="1"><td><strong><a href="#page-467">Chapter 19: Tessellation &amp; Terrains</a></strong></td><td>467</td></tr>
<tr data-level="1"><td><strong><a href="#page-500">Chapter 20: Fragment Post-Processing</a></strong></td><td>500</td></tr>
<tr data-level="1"><td><strong><a href="#page-519">Chapter 21: Image-Based Lighting</a></strong></td><td>519</td></tr>
<tr data-level="1"><td><strong><a href="#page-555">Chapter 22: Reﬂection &amp; Refraction</a></strong></td><td>555</td></tr>
<tr data-level="1"><td><strong><a href="#page-580">Chapter 23: Animation</a></strong></td><td>580</td></tr>
<tr data-level="1"><td><strong><a href="#page-604">Chapter 24: Character Animation</a></strong></td><td>604</td></tr>
<tr data-level="1"><td><strong><a href="#page-634">Chapter 25: Managing Resources</a></strong></td><td>634</td></tr>
<tr data-level="1"><td><strong><a href="#page-657">Chapter 26: Indirect Command Encoding</a></strong></td><td>657</td></tr>
<tr data-level="1"><td><strong><a href="#page-671">Section IV: Pushing the GPU</a></strong></td><td>671</td></tr>
<tr data-level="1"><td><strong><a href="#page-672">Chapter 27: GPU Command Encoding</a></strong></td><td>672</td></tr>
<tr data-level="1"><td><strong><a href="#page-689">Chapter 28: Geometry Creation with Mesh Shaders</a></strong></td><td>689</td></tr>
<tr data-level="1"><td><strong><a href="#page-713">Chapter 29: Metal Performance Shaders</a></strong></td><td>713</td></tr>
<tr data-level="1"><td><strong><a href="#page-732">Chapter 30: Proﬁling</a></strong></td><td>732</td></tr>
<tr data-level="1"><td><strong><a href="#page-762">Chapter 31: Best Practices</a></strong></td><td>762</td></tr>
<tr data-level="1"><td><strong><a href="#page-772">Conclusion</a></strong></td><td>772</td></tr>
</table>

<a id="page-5"></a>

# Table of Contents: Extended

<table data-pdf-contents="true">
<tr><th>Entry</th><th>Page</th></tr>
<tr data-level="1"><td><strong><a href="#page-16">Book License</a></strong></td><td>16</td></tr>
<tr data-level="1"><td><strong><a href="#page-17">Before You Begin</a></strong></td><td>17</td></tr>
<tr data-level="1"><td><strong><a href="#page-18">What You Need</a></strong></td><td>18</td></tr>
<tr data-level="1"><td><strong><a href="#page-19">Book Source Code &amp; Forums</a></strong></td><td>19</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-21">About the Authors</a></td><td>21</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-21">About the Editors</a></td><td>21</td></tr>
<tr data-level="1"><td><strong><a href="#page-22">Acknowledgments</a></strong></td><td>22</td></tr>
<tr data-level="1"><td><strong><a href="#page-23">Introduction</a></strong></td><td>23</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-23">About This Book</a></td><td>23</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-24">How Did Metal Come to Life?</a></td><td>24</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-25">Why Would You Use Metal?</a></td><td>25</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-26">When Should You Use Metal?</a></td><td>26</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-27">Who This Book Is For?</a></td><td>27</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-27">How to Read This Book?</a></td><td>27</td></tr>
<tr data-level="1"><td><strong><a href="#page-28">Section I: Beginning Metal</a></strong></td><td>28</td></tr>
<tr data-level="1"><td><strong><a href="#page-29">Chapter 1: Hello, Metal!</a></strong></td><td>29</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-30">What is Rendering?</a></td><td>30</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-32">What is a Frame?</a></td><td>32</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-32">Your First Metal App</a></td><td>32</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-33">The Metal View</a></td><td>33</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-39">Rendering</a></td><td>39</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-44">Challenge</a></td><td>44</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-45">Key Points</a></td><td>45</td></tr>
<tr data-level="1"><td><strong><a href="#page-46">Chapter 2: 3D Models</a></strong></td><td>46</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-47">What Are 3D Models?</a></td><td>47</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-51">Creating Models With Blender</a></td><td>51</td></tr>
</table>

<a id="page-6"></a>

<table data-pdf-contents="true">
<tr><th>Entry</th><th>Page</th></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-52">3D File Formats</a></td><td>52</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-53">Exporting to Blender</a></td><td>53</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-55">The USD File Format</a></td><td>55</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-60">Materials</a></td><td>60</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-60">Material Groups</a></td><td>60</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-62">Vertex Descriptors</a></td><td>62</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-66">Metal Coordinate System</a></td><td>66</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-68">Submeshes</a></td><td>68</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-71">Challenge</a></td><td>71</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-72">Key Points</a></td><td>72</td></tr>
<tr data-level="1"><td><strong><a href="#page-73">Chapter 3: The Rendering Pipeline</a></strong></td><td>73</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-74">The GPU and CPU</a></td><td>74</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-75">The Metal Project</a></td><td>75</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-85">The Render Pipeline</a></td><td>85</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-96">Challenge</a></td><td>96</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-97">Key Points</a></td><td>97</td></tr>
<tr data-level="1"><td><strong><a href="#page-98">Chapter 4: The Vertex Function</a></strong></td><td>98</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-98">Shader Functions</a></td><td>98</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-99">The Starter Project</a></td><td>99</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-100">Rendering a Quad</a></td><td>100</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-104">Calculating Positions</a></td><td>104</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-106">More Efﬁcient Rendering</a></td><td>106</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-108">Vertex Descriptors</a></td><td>108</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-111">Adding Another Vertex Attribute</a></td><td>111</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-115">Rendering Points</a></td><td>115</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-116">Challenge</a></td><td>116</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-118">Key Points</a></td><td>118</td></tr>
<tr data-level="1"><td><strong><a href="#page-119">Chapter 5: 3D Transformations</a></strong></td><td>119</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-120">Transformations</a></td><td>120</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-121">The Starter Project &amp; Setup</a></td><td>121</td></tr>
</table>

<a id="page-7"></a>

<table data-pdf-contents="true">
<tr><th>Entry</th><th>Page</th></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-122">Translation</a></td><td>122</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-122">Vectors &amp; Matrices</a></td><td>122</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-125">Creating a Matrix</a></td><td>125</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-127">Scaling</a></td><td>127</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-129">Rotation</a></td><td>129</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-133">Key Points</a></td><td>133</td></tr>
<tr data-level="1"><td><strong><a href="#page-134">Chapter 6: Coordinate Spaces</a></strong></td><td>134</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-139">The Starter Project</a></td><td>139</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-140">Uniforms</a></td><td>140</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-146">Projection</a></td><td>146</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-151">Refactoring the Model Matrix</a></td><td>151</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-154">Key Points</a></td><td>154</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-154">Where to Go From Here?</a></td><td>154</td></tr>
<tr data-level="1"><td><strong><a href="#page-155">Chapter 7: The Fragment Function</a></strong></td><td>155</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-156">The Starter Project</a></td><td>156</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-157">Screen Space</a></td><td>157</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-160">Metal Standard Library Functions</a></td><td>160</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-166">Normals</a></td><td>166</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-168">Loading the Train Model With Normals</a></td><td>168</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-171">Depth</a></td><td>171</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-174">Hemispheric Lighting</a></td><td>174</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-176">Challenge</a></td><td>176</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-177">Key Points</a></td><td>177</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-177">Where to Go From Here?</a></td><td>177</td></tr>
<tr data-level="1"><td><strong><a href="#page-178">Chapter 8: Textures</a></strong></td><td>178</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-179">Textures and UV Maps</a></td><td>179</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-182">The Starter App</a></td><td>182</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-190">The Ground Plane</a></td><td>190</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-191">The Asset Catalog</a></td><td>191</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-195">sRGB Color Space</a></td><td>195</td></tr>
</table>

<a id="page-8"></a>

<table data-pdf-contents="true">
<tr><th>Entry</th><th>Page</th></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-197">Capture GPU Workload</a></td><td>197</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-202">Samplers</a></td><td>202</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-206">Mipmaps</a></td><td>206</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-213">Challenge</a></td><td>213</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-214">Key Points</a></td><td>214</td></tr>
<tr data-level="1"><td><strong><a href="#page-215">Chapter 9: Navigating a 3D Scene</a></strong></td><td>215</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-216">The Starter Project</a></td><td>216</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-216">Scenes</a></td><td>216</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-218">Cameras</a></td><td>218</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-223">Input</a></td><td>223</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-225">Delta Time</a></td><td>225</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-231">Mouse and Trackpad Input</a></td><td>231</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-232">Arcball Camera</a></td><td>232</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-237">Orthographic Projection</a></td><td>237</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-242">Challenge</a></td><td>242</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-243">Key Points</a></td><td>243</td></tr>
<tr data-level="1"><td><strong><a href="#page-244">Chapter 10: Lighting Fundamentals</a></strong></td><td>244</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-245">The Starter Project</a></td><td>245</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-246">Representing Color</a></td><td>246</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-248">Normals</a></td><td>248</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-249">Light Types</a></td><td>249</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-249">Directional Light</a></td><td>249</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-252">The Phong Reﬂection Model</a></td><td>252</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-253">The Dot Product</a></td><td>253</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-256">Creating Shared Functions in C++</a></td><td>256</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-265">Point Lights</a></td><td>265</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-268">Spotlights</a></td><td>268</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-271">Key Points</a></td><td>271</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-271">Where to Go From Here?</a></td><td>271</td></tr>
<tr data-level="1"><td><strong><a href="#page-272">Section II: Intermediate Metal</a></strong></td><td>272</td></tr>
</table>

<a id="page-9"></a>

<table data-pdf-contents="true">
<tr><th>Entry</th><th>Page</th></tr>
<tr data-level="1"><td><strong><a href="#page-273">Chapter 11: Maps &amp; Materials</a></strong></td><td>273</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-274">Physically Based Rendering (PBR)</a></td><td>274</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-276">The Starter App</a></td><td>276</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-277">Examining USD Files in Reality Composer Pro</a></td><td>277</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-280">Materials</a></td><td>280</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-284">Surface Roughness</a></td><td>284</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-287">Normal Maps</a></td><td>287</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-294">Using Normal Maps</a></td><td>294</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-302">Challenge</a></td><td>302</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-303">Where to Go From Here?</a></td><td>303</td></tr>
<tr data-level="1"><td><strong><a href="#page-304">Chapter 12: Render Passes</a></strong></td><td>304</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-305">Render Passes</a></td><td>305</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-307">Object Picking</a></td><td>307</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-307">The Starter App</a></td><td>307</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-308">Setting up Render Passes</a></td><td>308</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-309">Creating a UInt32 Texture</a></td><td>309</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-313">Adding the Render Pass to Renderer</a></td><td>313</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-314">Adding the Shader Function</a></td><td>314</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-317">Adding the Depth Attachment</a></td><td>317</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-320">Load &amp; Store Actions</a></td><td>320</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-321">Reading the Object ID Texture</a></td><td>321</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-325">Key Points</a></td><td>325</td></tr>
<tr data-level="1"><td><strong><a href="#page-326">Chapter 13: Shadows</a></strong></td><td>326</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-327">Shadow Maps</a></td><td>327</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-328">The Starter Project</a></td><td>328</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-340">Identifying Problems</a></td><td>340</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-341">Visualizing the Problems</a></td><td>341</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-345">Solving the Problems</a></td><td>345</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-347">Cascaded Shadow Mapping</a></td><td>347</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-348">Key Points</a></td><td>348</td></tr>
</table>

<a id="page-10"></a>

<table data-pdf-contents="true">
<tr><th>Entry</th><th>Page</th></tr>
<tr data-level="1"><td><strong><a href="#page-349">Chapter 14: Deferred Rendering</a></strong></td><td>349</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-352">The Starter Project</a></td><td>352</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-353">The G-buffer Pass</a></td><td>353</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-363">Updating Renderer</a></td><td>363</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-364">The Lighting Shader Functions</a></td><td>364</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-367">Adding Point Lights</a></td><td>367</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-374">Blending</a></td><td>374</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-378">Key Points</a></td><td>378</td></tr>
<tr data-level="1"><td><strong><a href="#page-379">Chapter 15: Tile-Based Deferred Rendering</a></strong></td><td>379</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-381">Programmable Blending</a></td><td>381</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-381">Tiled Deferred Rendering</a></td><td>381</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-382">The Starter Project</a></td><td>382</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-392">Stencil Tests</a></td><td>392</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-396">Create the Stencil Texture</a></td><td>396</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-397">Conﬁgure the Stencil Operation</a></td><td>397</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-402">Masking the Sky</a></td><td>402</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-403">Challenge</a></td><td>403</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-404">Key Points</a></td><td>404</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-404">Where to Go From Here?</a></td><td>404</td></tr>
<tr data-level="1"><td><strong><a href="#page-405">Chapter 16: GPU Compute Programming</a></strong></td><td>405</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-406">The Starter Project</a></td><td>406</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-407">Winding Order and Culling</a></td><td>407</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-408">Reversing the Model on the CPU</a></td><td>408</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-410">Compute Processing</a></td><td>410</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-414">Reversing the Gnome Using GPU Compute Processing</a></td><td>414</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-416">The Kernel Function</a></td><td>416</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-418">Atomic Functions</a></td><td>418</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-420">Key Points</a></td><td>420</td></tr>
<tr data-level="1"><td><strong><a href="#page-421">Chapter 17: Particle Systems</a></strong></td><td>421</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-422">Particle</a></td><td>422</td></tr>
</table>

<a id="page-11"></a>

<table data-pdf-contents="true">
<tr><th>Entry</th><th>Page</th></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-423">Emitter</a></td><td>423</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-423">The Starter Project</a></td><td>423</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-424">Creating a Particle and Emitter</a></td><td>424</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-427">The Fireworks Pass</a></td><td>427</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-431">Particle Dynamics</a></td><td>431</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-432">Implementing Particle Physics</a></td><td>432</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-433">Particle Systems</a></td><td>433</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-436">Rendering a Particle System</a></td><td>436</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-442">Conﬁguring Particle Effects</a></td><td>442</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-444">Fire</a></td><td>444</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-445">Key Points</a></td><td>445</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-445">Where to Go From Here?</a></td><td>445</td></tr>
<tr data-level="1"><td><strong><a href="#page-446">Chapter 18: Particle Behavior</a></strong></td><td>446</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-447">Behavioral Animation</a></td><td>447</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-448">Swarming Behavior</a></td><td>448</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-449">The Starter Project</a></td><td>449</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-452">Velocity</a></td><td>452</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-454">Behavioral Rules</a></td><td>454</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-465">Key Points</a></td><td>465</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-465">Where to Go From Here?</a></td><td>465</td></tr>
<tr data-level="1"><td><strong><a href="#page-466">Section III: Advanced Metal</a></strong></td><td>466</td></tr>
<tr data-level="1"><td><strong><a href="#page-467">Chapter 19: Tessellation &amp; Terrains</a></strong></td><td>467</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-468">Tessellation</a></td><td>468</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-468">The Starter Project</a></td><td>468</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-473">The Tessellation Kernel</a></td><td>473</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-481">Multiple Patches</a></td><td>481</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-482">Tessellation By Distance</a></td><td>482</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-487">Displacement</a></td><td>487</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-493">Shading By Slope</a></td><td>493</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-496">Challenge</a></td><td>496</td></tr>
</table>

<a id="page-12"></a>

<table data-pdf-contents="true">
<tr><th>Entry</th><th>Page</th></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-498">Key Points</a></td><td>498</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-499">Where to Go From Here?</a></td><td>499</td></tr>
<tr data-level="1"><td><strong><a href="#page-500">Chapter 20: Fragment Post-Processing</a></strong></td><td>500</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-501">The Starter App</a></td><td>501</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-502">Alpha Testing</a></td><td>502</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-504">Depth Testing</a></td><td>504</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-504">Stencil Testing</a></td><td>504</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-504">Scissor Testing</a></td><td>504</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-505">Alpha Blending</a></td><td>505</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-507">Opacity</a></td><td>507</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-507">Blending</a></td><td>507</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-513">Antialiasing</a></td><td>513</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-516">Fog</a></td><td>516</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-518">Key Points</a></td><td>518</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-518">Where to Go From Here?</a></td><td>518</td></tr>
<tr data-level="1"><td><strong><a href="#page-519">Chapter 21: Image-Based Lighting</a></strong></td><td>519</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-520">The Starter Project</a></td><td>520</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-520">The Skybox</a></td><td>520</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-527">Procedural Skies</a></td><td>527</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-535">Reﬂection</a></td><td>535</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-539">Image-Based Lighting</a></td><td>539</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-553">Challenge</a></td><td>553</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-554">Key Points</a></td><td>554</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-554">Where to Go From Here?</a></td><td>554</td></tr>
<tr data-level="1"><td><strong><a href="#page-555">Chapter 22: Reﬂection &amp; Refraction</a></strong></td><td>555</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-556">The Starter Project</a></td><td>556</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-557">Rendering Rippling Water</a></td><td>557</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-558">1. Creating the Water Surface</a></td><td>558</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-560">2. Rendering the Reﬂection</a></td><td>560</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-566">3. Creating Clipping Planes</a></td><td>566</td></tr>
</table>

<a id="page-13"></a>

<table data-pdf-contents="true">
<tr><th>Entry</th><th>Page</th></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-569">4. Rippling Normal Maps</a></td><td>569</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-571">5. Adding Refraction</a></td><td>571</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-574">6. The Fresnel Effect</a></td><td>574</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-576">7. Adding Smoothness Using a Depth Texture</a></td><td>576</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-579">Key Points</a></td><td>579</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-579">Where to Go From Here?</a></td><td>579</td></tr>
<tr data-level="1"><td><strong><a href="#page-580">Chapter 23: Animation</a></strong></td><td>580</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-581">The Starter Project</a></td><td>581</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-581">Animation</a></td><td>581</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-582">Procedural Animation</a></td><td>582</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-583">Animation Using Physics</a></td><td>583</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-587">Keyframes</a></td><td>587</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-593">Quaternions</a></td><td>593</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-597">USD and USDZ Files</a></td><td>597</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-598">Animating Meshes</a></td><td>598</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-603">Key Points</a></td><td>603</td></tr>
<tr data-level="1"><td><strong><a href="#page-604">Chapter 24: Character Animation</a></strong></td><td>604</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-605">Skeletal Animation</a></td><td>605</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-611">The Starter App</a></td><td>611</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-612">Implementing Skeletal Animation</a></td><td>612</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-614">Initializing Data</a></td><td>614</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-617">The Math of Striking a Pose</a></td><td>617</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-624">Joints and Weights Vertex Data</a></td><td>624</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-625">Transfer the Data to the GPU</a></td><td>625</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-626">Updating the Vertex Shader</a></td><td>626</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-629">Function Specialization</a></td><td>629</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-633">Key Points</a></td><td>633</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-633">Where to Go From Here?</a></td><td>633</td></tr>
<tr data-level="1"><td><strong><a href="#page-634">Chapter 25: Managing Resources</a></strong></td><td>634</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-635">The Starter Project</a></td><td>635</td></tr>
</table>

<a id="page-14"></a>

<table data-pdf-contents="true">
<tr><th>Entry</th><th>Page</th></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-637">Argument Buffers</a></td><td>637</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-646">Resource Heaps</a></td><td>646</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-653">Residency Sets</a></td><td>653</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-656">Key Points</a></td><td>656</td></tr>
<tr data-level="1"><td><strong><a href="#page-657">Chapter 26: Indirect Command Encoding</a></strong></td><td>657</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-658">The Starter Project</a></td><td>658</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-660">Indirect Command Buffers (ICB)</a></td><td>660</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-670">Key Points</a></td><td>670</td></tr>
<tr data-level="1"><td><strong><a href="#page-671">Section IV: Pushing the GPU</a></strong></td><td>671</td></tr>
<tr data-level="1"><td><strong><a href="#page-672">Chapter 27: GPU Command Encoding</a></strong></td><td>672</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-673">The Starter Project</a></td><td>673</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-687">Key Points</a></td><td>687</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-688">Where to Go From Here?</a></td><td>688</td></tr>
<tr data-level="1"><td><strong><a href="#page-689">Chapter 28: Geometry Creation with Mesh Shaders</a></strong></td><td>689</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-689">The Mesh Shader Pipeline</a></td><td>689</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-691">The Starter Project</a></td><td>691</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-691">Render a Triangle With a Mesh Shader</a></td><td>691</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-697">Procedural Grass Generation</a></td><td>697</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-708">Creating Randomness</a></td><td>708</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-710">Meshlet Culling</a></td><td>710</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-711">Challenge</a></td><td>711</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-712">Key Points</a></td><td>712</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-712">Where to Go From Here?</a></td><td>712</td></tr>
<tr data-level="1"><td><strong><a href="#page-713">Chapter 29: Metal Performance Shaders</a></strong></td><td>713</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-714">The Sobel Filter</a></td><td>714</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-716">Image Processing</a></td><td>716</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-720">The Starter Project</a></td><td>720</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-722">The Blit Command Encoder</a></td><td>722</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-724">Gaussian Blur</a></td><td>724</td></tr>
</table>

<a id="page-15"></a>

<table data-pdf-contents="true">
<tr><th>Entry</th><th>Page</th></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-726">Matrix / Vector Mathematics</a></td><td>726</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-731">Challenge</a></td><td>731</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-731">Key Points</a></td><td>731</td></tr>
<tr data-level="1"><td><strong><a href="#page-732">Chapter 30: Proﬁling</a></strong></td><td>732</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-733">The Starter App</a></td><td>733</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-735">Proﬁling</a></td><td>735</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-739">GPU Workload Capture</a></td><td>739</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-745">GPU Timeline</a></td><td>745</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-748">Instancing</a></td><td>748</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-750">Inspecting Shaders</a></td><td>750</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-754">CPU-GPU Synchronization</a></td><td>754</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-759">MetalFX Upscaling</a></td><td>759</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-760">Visibility Culling</a></td><td>760</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-761">Key Points</a></td><td>761</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-761">Where to Go From Here?</a></td><td>761</td></tr>
<tr data-level="1"><td><strong><a href="#page-762">Chapter 31: Best Practices</a></strong></td><td>762</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-763">General Performance Best Practices</a></td><td>763</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-766">Memory Bandwidth Best Practices</a></td><td>766</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-769">Memory Footprint Best Practices</a></td><td>769</td></tr>
<tr data-level="2"><td>&nbsp;&nbsp;&nbsp;&nbsp;<a href="#page-771">Where to Go From Here?</a></td><td>771</td></tr>
<tr data-level="1"><td><strong><a href="#page-772">Conclusion</a></strong></td><td>772</td></tr>
</table>

<a id="page-16"></a>

# L

# Book License

By purchasing _Metal by Tutorials_, you have the following license:

• You are allowed to use and/or modify the source code in Metal by Tutorials in as many apps as you want, with no attribution required.

• You are allowed to use and/or modify all art, images and designs that are included in Metal by Tutorials in as many apps as you want, but must include this attribution line somewhere inside your app: “Artwork/images/designs: from Metal by Tutorials, available at www.kodeco.com”.

• The source code included in Metal by Tutorials is for your personal use only. You are NOT allowed to distribute or sell the source code in Metal by Tutorials without prior authorization.

• This book is for your personal use only. You are NOT allowed to reproduce or transmit any part of this book by any means, electronic or mechanical, including photocopying, recording, etc. without previous authorization. You may not sell digital versions of this book or distribute them to friends, coworkers or students without prior authorization. They need to purchase their own copies.

All materials provided with this book are provided on an “as is” basis, without warranty of any kind, express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose and noninfringement. In no event shall the authors or copyright holders be liable for any claim, damages or other liability, whether in an action of contract, tort or otherwise, arising from, out of or in connection with the software or the use or other dealings in the software.

All trademarks and registered trademarks appearing in this guide are the properties of their respective owners.

<a id="page-17"></a>

# **Before You Begin**

This section tells you a few things you need to know before you get started, such as what you’ll need for hardware and software, where to find the project files for this book and more.

<a id="page-18"></a>

# i

# What You Need

To follow along with the tutorials in this book, you need the following:

• A Metal-capable Mac running macOS Sonoma 14.0 or later. All Macs built since 2012 should run Metal, although not all of them will be able to run the most recent features in Metal 3. Nvidia GPUs will have issues, in some cases serious, as drivers have not been updated since macOS High Sierra. One chapter includes Apple GPU-specific code, for which you’ll need either an M1 GPU or a recent iPhone or iPad.

• Xcode 15.0 or later.

• [optional] A Metal-capable iPhone or iPad running iOS 17 or later. Any iOS device running the A7 chip or later will run Metal. The latest features, such as tile shading and imageblocks, will only run on the A11 (or later) chipset. The projects will build and run on macOS, and most of them will run on the iOS Simulator, so using an iOS device is optional. If you wish to make an iOS game, the game engine you build while reading this book will have an iOS target as well.

<a id="page-19"></a>

# ii

# Book Source Code &amp; Forums

## Where to Download the Materials for This Book

The materials for this book can be cloned or downloaded from the GitHub book materials repository:

• https://github.com/kodecocodes/met-materials/tree/editions/5.0

## **Forums**

We’ve also set up an official forum for the book at https://forums.kodeco.com/c/ books/metal-by-tutorials. This is a great place to ask questions about the book or to submit any errors you may find.

<a id="page-20"></a>

“To Warren Moore, who first made it possible for me to learn

Metal, to my wonderful children Robin and Kayla, and to the

Kodeco forum community for their contributions.”

— Caroline Begbie

“To my wife, Adina, and my son, Victor Nicholas, without whose patience, support and understanding I could not have

made it. To Warren Moore who first whet my appetite for Metal, offered his advice when needed and motivated me to

get involved with Metal too. To Chris Wood who taught me that most of the times all you need to render is a ray, a camera

and a few distance fields. To Simon Gladman whose amazing

work with compute kernels inspired me to write more about

particles and fluid dynamics. To Jeff Biggus who keeps the

GPU programming community in Chicago alive. Our daily

conversations motivate me to stay hungry for more. To everyone else who believes in me. A huge Thanks to all of

you!”

— Marius Horga

<a id="page-21"></a>

_About the Team_

## **About the Authors**

![Figure](Metal_by_Tutorials_v500mpdf/4ac124320e7a77a41114b58a.png)

Caroline Begbie is a co-author of this book. Caroline is an indie iOS developer. When she’s not developing, she’s playing around with 2D and 3D animation software, or planning The Big Lap around Australia. She has previously taught the elderly how to use their computers, done marionette shows for pre-schools, and created accounting and stock control systems for mining companies.

![Figure](Metal_by_Tutorials_v500mpdf/bbc35fd533c379bc6f6cb08d.png)

Marius Horga is a co-author of this book. Marius is an iOS developer and Metal API blogger. He is also a computer scientist. He has more than a decade of experience with systems, support, integration and development. You can often see him on Twitter talking about Metal, GPGPU, games and 3D graphics. When he’s away from computers, he enjoys music, biking or stargazing.

## **About the Editors**

![Figure](Metal_by_Tutorials_v500mpdf/330dcbd45b2b490cb72b8eb8.png)

Adrian Strahan is the technical editor of this book. Adrian is a lead iOS developer working for a leading UK bank. When he’s not sat in front of a computer, he enjoys watching sport, listening to music, building Lego and trying to keep fit and healthy.

![Figure](Metal_by_Tutorials_v500mpdf/eeebdf7d580193761e0f1cce.png)

Tammy Coron is the final pass editor of this book. Tammy is an independent creative professional, author of Apple Game Frameworks and Technologies, and the maker behind the AdventureGameKit — a custom SpriteKit framework for building point and click adventure games. Find out more at tammycoron.com.

<a id="page-22"></a>

# v

# Acknowledgments

Many of the models and images used in this book were made by the authors and the Kodeco team. In some cases, the authors used public domain or CC By 4.0, commercial allowed models and images and included links and licences in either the projects’ Models folder or references.markdown for the chapter.

<a id="page-23"></a>

# vi

# Introduction

Welcome to Metal by Tutorials!

Metal is a unified, low-level, low-overhead application programming interface (API) for the graphics processing unit, or GPU. It’s unified because it applies to both 3D graphics and data-parallel computation paradigms. Metal is a low-level API because it provides programmers near-direct access to the GPU. Finally, Metal is a low-overhead API because it reduces the runtime cost by multi-threading and pre-compiling of resources.

But beyond the technical definition, Metal is the most appropriate way to use the parallel processing power of Apple GPUs to visualize data or solve numerical challenges. It’s also tailored to be used for machine learning, image/video processing or, as this book describes, graphics rendering.

## **About This Book**

This book introduces you to low-level graphics programming in Metal — Apple’s framework for programming on the graphics processing unit (GPU). As you progress through this book, you’ll learn many of the fundamentals that go into making a game engine and gradually put together your own engine. Once your game engine is complete, you’ll be able to put together 3D scenes and program your own simple 3D games. Because you’ll have built your 3D game engine from scratch, you’ll be able to customize every aspect of what you see on your screen.

<a id="page-24"></a>

## **How Did Metal Come to Life?**

Historically, you had two choices to take advantage of the power of the GPU: OpenGL and the Windows-only DirectX. In 2013, the GPU vendor AMD announced the Mantle project in an effort to revamp GPU APIs and come up with an alternative to Direct3D (which is part of DirectX) and OpenGL. AMD were the first to create a true low-overhead API for low-level access to the GPU. Mantle promised to be able to generate up to 9 times more draw calls (the number of objects drawn to the screen) than similar APIs and also introduced asynchronous command queues so that graphics and compute workloads could be run in parallel. Unfortunately, the project was terminated before it could become a mainstream API.

Metal was announced at the Worldwide Developers Conference (WWDC) on June 2, 2014 and was initially made available only on A7 or newer GPUs. Apple created a new language to program the GPU directly via shader functions. This is the Metal Shading Language (MSL) based on the C++11 specification. A year later at WWDC 2015, Apple announced two Metal sub-frameworks: MetalKit and Metal Performance Shaders (MPS). In 2018, MPS made a spectacular debut as a Ray Tracing accelerator.

The API continued its evolution to work with the exciting features of the new Apple GPUS designed in-house by Apple. Metal 2 added support for Virtual Reality (VR), Augmented Reality (AR) and accelerated machine learning (ML), among many new features, including image blocks, tile shading and threadgroup sharing. Metal Shading Language is now based on the C++14 specification.

In 2022, Apple introduced Metal 3 with a new framework MetalFX for upscaling lower resolutions. Metal 3 features also include fast resource loading of textures directly from disk, mesh shaders for adding or reducing geometry and using C/C++ for Metal.

In 2025, Apple introduced Metal 4. This latest version improves command encoding and resource management. It supports machine learning and tensors. New API commands allow you to adopt Metal 4 gradually. This book doesn’t cover Metal 4, but when you have learned the vocabulary and concepts of Metal and Computer Graphics, you will be able to watch Apple’s introductory videos and understand what the changes are.

<a id="page-25"></a>

## **Why Would You Use Metal?**

Metal is a top-notch graphics API. That means Metal can empower graphics pipelines and, more specifically, game engines such as the following:

• Unity and Unreal Engine: The two leading cross-platform game engines today are ideal for game programmers who target a range of console, desktop and mobile devices. However, these engines haven’t always kept pace with new features in Metal. For example, tessellation was long delayed in Unity, and mesh shaders are still not fully supported. If you want to use cutting-edge Metal developments, and use the power of Apple silicon, you can’t always depend on third-party engines.

• Divinity - Original Sin 2: Larian Studios worked closely with Apple to bring their amazing AAA game to iPad, taking advantage of Metal and the Apple GPU hardware. It truly is a stunning visual experience.

• Cyberpunk 2077: This game, when the new version is released, will take full advantage of the power of Metal 4.

• Many Others: From notable game titles such as Hitman, BioShock, Deus Ex, Mafia, Starcraft, World of Warcraft, Fortnite, Unreal Tournament, Batman and even the beloved Minecraft.

But Metal isn’t limited to the world of gaming. There are many apps that benefit from GPU acceleration for image and video processing:

• Procreate: An app for sketching, painting and illustrating. Since converting to Metal, it runs four times faster than it did before.

• Pixelmator Pro: A Metal-based app that provides image distortion tools. In fact, they were able to implement a new painting engine and dynamic paint blending technology powered by Metal 2.

• Affinity Photo: Available on the iPad. According to the developer Serif, “Using Metal allows users to work easily on large, super high-resolution photographs, or complex compositions with potentially thousands of layers.”

• Blender: Apple developers contributed Metal code to the open-source Blender, supporting GPU rendering using Metal.

<a id="page-26"></a>

## **When Should You Use Metal?**

GPUs belong to a special class of computation that Flynn’s taxonomy terms Single Instruction Multiple Data (SIMD). Simply, GPUs are processors that are optimized for throughput (how much data can be processed in one unit of time), while CPUs are optimized for latency (how much time it takes a single unit of data to be processed). Most programs execute serially: they receive input, process it, provide output and then the cycle repeats.

Those cycles sometimes perform computationally-intensive tasks, such as large matrix multiplication, which would take CPUs a lot of time process serially, even in a multithreaded manner on a handful of cores.

In contrast, GPUs have hundreds or even thousands of cores which are smaller and have less memory than CPU cores, but perform fast parallel mathematical calculations.

Choose Metal when:

• You want to render 3D models as efficiently as possible.

• You want your game to have its own unique style, perhaps with custom lighting and shading.

• You will be performing intensive data processes, such as calculating and changing the color of each pixel on the screen every frame, as you would when processing images and video.

• You have large numerical problems, such as scientific simulations, that you can partition into independent sub-problems to be processed in parallel.

• You need to process multiple large datasets in parallel, such as when you train models for deep learning.

<a id="page-27"></a>

## **Who This Book Is For?**

This book is for intermediate Swift developers interested in learning 3D graphics or gaining a deeper understanding of how game engines work. If you don’t know Swift, you can still follow along, as all the code instructions are included in the book. You’ll gain general graphics knowledge, but it would be less confusing if you cover Swift basics first. We recommend the Swift Apprentice: Fundamentals book (https:// www.kodeco.com/books/swift-apprentice-fundamentals), available in our catalog.

A smattering of C++ knowledge would be useful too. The Metal Shader Language that you’ll use when writing GPU shader functions is based on C++. But, again, all the code you’ll need is included in the book.

## **How to Read This Book?**

If you’re a beginner to iOS/macOS development or Metal, you should read this book from cover to cover.

If you’re an advanced developer, or already have experience with Metal, you can skip from chapter to chapter or use this book as a reference.

<a id="page-28"></a>

# **Section I: Beginning Metal**

It takes a wealth of knowledge to render a simple triangle on the screen or animate game characters. This section will guide you through the necessary basics of vertex wrangling, lighting, textures and creating a game scene. If you’re worried about the math, don’t be! Although computer graphics is highly math-intensive, each chapter explains everything you need, and you’ll get experience creating and rendering models.

<a id="page-29"></a>

# 1

# Chapter 1: Hello, Metal!

You’ve been formally introduced to Metal and discovered its history and why you should use it. Now you’re going to to try it out for yourself in a Swift playground. To get started, you’ll render this sphere on the screen:

![Figure](Metal_by_Tutorials_v500mpdf/79ede577f50b00e3c56844c6.png)

_The final result_

It may not look exciting, but this is a great starting point because the exercise touches on almost every part of the rendering process. But before you get started, it’s important to understand the terms rendering and frames.

<a id="page-30"></a>

## **What is Rendering?**

In 3D computer graphics, you take a bunch of points in 3D space, join them together and create a 2D image on the screen. This image is known as a render.

Rendering an image from points involves calculating light and shade for each pixel on the screen. Light bounces around a scene, so you have to decide how complicated your lighting is and how long each image takes to render. A single image in a Pixar movie might take days to render, but games require real-time rendering, where you see the image immediately.

There are many ways to render a 3D image, but most start with a model built in a modeling app such as Blender or Maya. Take, for example, this train model that was built in Blender:

![Figure](Metal_by_Tutorials_v500mpdf/c6e049c83b9217d5b6b80000.png)

_A train model in Blender_

This model, like all other models, is made up of vertices. A vertex refers to a point in three dimensional space where two or more lines, curves or edges of a geometrical shape meet, such as the corners of a cube.  The number of vertices in a model may vary from a handful, as in a cube, to thousands or even millions in more complex models.

<a id="page-31"></a>

A 3D renderer will read in these vertices using model loader code, which parses the list of vertices. The renderer then passes the vertices to the GPU, where shader functions process the vertices to create the final image or texture to be sent back to the CPU and displayed on the screen.

The following render uses the 3D train model and some different shading techniques to make it appear as if the train were made of shiny copper:

![Figure](Metal_by_Tutorials_v500mpdf/346bca576bc286897b3d7d60.png)

_Shading techniques cause reflection_

The entire process, from importing a model’s vertices to generating the final image on your screen, is commonly known as the rendering pipeline. The rendering pipeline is a list of commands sent to the GPU, along with resources (vertices, materials and lights) that make up the final image.

The pipeline includes programmable and non-programmable functions. The programmable parts of the pipeline are shader functions that run on the GPU, where you can manually influence the final look of your rendered models. You’ll learn more about these shader functions later in the book.

<a id="page-32"></a>

## **What is a Frame?**

A game wouldn’t be much fun if all it did was render a single still image. Moving a character around the screen in a fluid manner requires the GPU to render a still image roughly sixty times a second. Each still image is known as a frame, and the speed at which the images appear is known as the frame rate.

When your favorite game appears to stutter, it’s usually because of a decrease in the frame rate, especially if there’s an excessive amount of background processing eating away at the GPU. When designing a game, it’s important to balance the result you want with what the hardware can deliver.

While it might be cool to add real-time shadows, water reflections and millions of blades of animated grass — all of which you’ll learn how to do in this book — finding the right balance between what is possible and what the GPU can process in 1/60th of a second can be tough.

## **Your First Metal App**

In your first Metal app, the shape you’ll render will look more like a flat circle than a 3D sphere. That’s because your first model will not include any perspective or shading. However, its vertex mesh contains the full three-dimensional information.

The process of Metal rendering is much the same no matter the size and complexity of your app, and you’ll become very familiar with the following sequence of drawing your models on the screen:

![Figure](Metal_by_Tutorials_v500mpdf/cac0b8feeeb1b9f6769c23c2.png)

You may initially feel a little overwhelmed by the number of steps Metal requires, but don’t worry. You’ll always perform these steps in the same sequence, and they’ll gradually become second nature.

This chapter won’t go into detail on every step, but as you progress through the book, you’ll get more information as you need it. For now, concentrate on getting your first Metal app running.

<a id="page-33"></a>

## **Getting Started**

➤ Start Xcode, and create a new playground by selecting File ▸ New ▸ Playground… from the main menu. When prompted for a template, choose macOS Blank.

![Figure](Metal_by_Tutorials_v500mpdf/759fe1e6e30fc0aee332c113.png)

_The playground template_

➤ Name the playground Chapter1, and click Create.

➤ Next, delete everything in the playground.

## **The Metal View**

Now that you have a playground, you’ll create a view to render into.

➤ Import the two main frameworks that you’ll be using by adding this:

```
import PlaygroundSupport
import MetalKit
```

PlaygroundSupport lets you see live views in the assistant editor, and MetalKit is a framework that makes using Metal easier. MetalKit has a customized view named MTKView and many convenience methods for loading textures, working with Metal buffers and interfacing with another useful framework: Model I/O, which you’ll learn about later.

<a id="page-34"></a>

➤ Now, add this:

```
guard let device = MTLCreateSystemDefaultDevice() else {
  fatalError("GPU is not supported")
}
```

This code checks for a suitable GPU by creating a software GPU device that you can interface with:

➤ To set up the view, add this:

```
let frame = CGRect(x: 0, y: 0, width: 500, height: 500)
let view = MTKView(frame: frame, device: device)
view.clearColor
  = MTLClearColor(red: 1, green: 1, blue: 0.8, alpha: 1)
PlaygroundPage.current.liveView = view
```

This code configures an MTKView for the Metal renderer. MTKView is a subclass of NSView on macOS and of UIView on iOS. MTLClearColor represents an RGBA value — in this case, cream. The color value is stored in clearColor and is used to set the color of the view.

Run the playground to ensure you have no errors so far. The first time you run the playground, Xcode takes a while to compile and build. Nothing will show yet in Live View.

![Figure](Metal_by_Tutorials_v500mpdf/426bf3ee6fc34d61401b31f9.png)

_Live View_

<a id="page-35"></a>

Note: If you don’t see a Results and Live View window, you may accidentally have created an iOS playground instead of a macOS playground. Adjust the editor options to ensure you have Results selected

![Figure](Metal_by_Tutorials_v500mpdf/080b61095ac861f44d5c3eb5.png)

_Adjust Editor Options_

## **The Model**

Model I/O is a framework that integrates with Metal and SceneKit. Its main purpose is to load 3D models that were created in apps like Blender or Maya, and to set up data buffers for easier rendering.

Instead of loading a 3D model, you’ll load a Model I/O basic 3D shape, also called a primitive. A 3D primitive is typically a cube, a sphere, a cylinder or a torus.

➤ Add this code to the end of the playground:

```
// 1
let allocator = MTKMeshBufferAllocator(device: device)
// 2
let mdlMesh = MDLMesh(
  sphereWithExtent: [0.75, 0.75, 0.75],
  segments: [30, 30],
  inwardNormals: false,
  geometryType: .triangles,
  allocator: allocator)
// 3
let mesh = try MTKMesh(mesh: mdlMesh, device: device)
```

<a id="page-36"></a>

Going through the code:

1. The allocator manages the memory for the mesh data.

2. Model I/O creates a sphere with the specified size and returns an MDLMesh with all the vertex information in data buffers.

3. For Metal to be able to use the mesh, you convert it from a Model I/O mesh to a MetalKit mesh.

## **Queues, Buffers and Encoders**

Note: There will be a lot of boiler-plate code to get to your first render. Don’t get overwhelmed, and don’t try and learn all the technical terms at once. Each app will generally start in the same way, and over the following chapters, you’ll gradually become accustomed to setting up rendering in Metal.

Each frame consists of commands that you send to the GPU. You wrap up these commands in a render command encoder. Command buffers organize these command encoders and a command queue organizes the command buffers.

![Figure](Metal_by_Tutorials_v500mpdf/f002e6a41a812362fd203862.png)

➤ Add this code to create a command queue:

`let commandQueue = device.makeCommandQueue()!`

You should set up the device and the command queue at the start of your app, and generally, you should use the same device and command queue throughout.

Each render pass must complete as quickly as possible, so you’ll pre-load objects at the start of your app. You’ll load models into buffers, generate shader functions and create pipeline state objects.

<a id="page-37"></a>

On each frame, you’ll create a command buffer and at least one render command encoder that describes the render pass. The render command encoder is a lightweight object that sets the GPU’s pipeline state and tells the GPU which buffers to use during the render pass.

![Figure](Metal_by_Tutorials_v500mpdf/8c429d578b21dfee6ea9456c.png)

## **Shader Functions**

Shader functions are small programs that run on the GPU. You write these programs in the Metal Shading Language, which is a subset of C++.

➤ Normally, you’d create a separate file with a .metal extension specifically for shader functions but for now, create a multi-line string containing the shader function code, and add it to your playground:

```
let shaders = """
#include <metal_stdlib>
using namespace metal;

struct VertexIn {
  float4 position [[attribute(0)]];
};

vertex float4 vertex_main(const VertexIn vertex_in [[stage_in]])
{
  return vertex_in.position;
}

fragment float4 fragment_main() {
  return float4(1, 0, 0, 1);
}
"""
```

<a id="page-38"></a>

There are two shader functions in here: a vertex function named vertex\_main and a fragment function named fragment\_main. The vertex function is where you usually manipulate vertex positions and the fragment function is where you specify the pixel color.

To set up a Metal library containing these two functions, add the following:

```
let library = try device.makeLibrary(source: shaders, options:
nil)
let vertexFunction = library.makeFunction(name: "vertex_main")
let fragmentFunction = library.makeFunction(name:
"fragment_main")
```

The compiler will check that these functions exist and make them available to a pipeline descriptor.

## **The Pipeline State**

In Metal, you set up a pipeline state for the GPU. By setting up this state, you’re telling the GPU that nothing will change until the state changes. With the GPU in a fixed state, it can run more efficiently. The pipeline state contains all sorts of information that the GPU needs, such as which pixel format it should use and whether it should render with depth. The pipeline state also holds the vertex and fragment functions that you just created.

However, you don’t create a pipeline state directly, rather you create it through a descriptor. This descriptor holds everything the pipeline needs to know, and you only change the necessary properties for your particular rendering situation.

➤ Add this code:

```
let pipelineDescriptor = MTLRenderPipelineDescriptor()
pipelineDescriptor.colorAttachments[0].pixelFormat = .bgra8Unorm
pipelineDescriptor.vertexFunction = vertexFunction
pipelineDescriptor.fragmentFunction = fragmentFunction
```

Here, you specified the pixel format to be four 8-bit unsigned integers with color pixel order of blue/green/red/alpha. You also set the two shader functions.

<a id="page-39"></a>

You’ll describe to the GPU how the vertices are laid out in memory using a vertex descriptor. Model I/O automatically creates a vertex descriptor when it loads the sphere mesh, so you can just use that one.

➤ Add this code:

```
pipelineDescriptor.vertexDescriptor =
  MTKMetalVertexDescriptorFromModelIO(mesh.vertexDescriptor)
```

You’ve now set up the pipeline descriptor with the necessary information. MTLRenderPipelineDescriptor has many other properties, but for now, you’ll use the defaults.

➤ Now, add this code:

```
let pipelineState =
  try device.makeRenderPipelineState(descriptor:
pipelineDescriptor)
```

This code creates the pipeline state from the descriptor. Creating a pipeline state takes valuable processing time, so all of the above should be a one-time setup. In a real app, you might create many pipeline states to call different shading functions or use different vertex layouts.

## **Rendering**

From now on, the code should be performed every frame. MTKView has a delegate method that runs every frame, but as you’re doing a simple render which will simply fill out a static view, you don’t need to keep refreshing the screen every frame.

When performing graphics rendering, the GPU’s ultimate job is to output a single texture from a 3d scene. This texture is similar to the digital image created by a physical camera. The texture will be displayed on the device’s screen each frame.

## **Render Passes**

If you’re trying to achieve a realistic render, you’ll want to take into account shadows, lighting and reflections. Each of these takes a lot of calculation and is generally done in separate render passes. For example, a shadow render pass will render the entire scene of 3D models, but only retain grayscale shadow information.

<a id="page-40"></a>

A second render pass would render the models in full color. You can then combine the shadow and color textures to produce the final output texture that will go to the screen.

![Figure](Metal_by_Tutorials_v500mpdf/e6dc4bbfd7d8fe0239c5ab5a.png)

For the first part of this book, you’ll use a single render pass. Later, you’ll learn about multipass rendering.

Conveniently, MTKView provides a render pass descriptor that will hold a texture called the drawable.

➤ Add this code to the end of the playground:

```
// 1
guard let commandBuffer = commandQueue.makeCommandBuffer(),
// 2
  let renderPassDescriptor = view.currentRenderPassDescriptor,
// 3
  let renderEncoder = commandBuffer.makeRenderCommandEncoder(
    descriptor: renderPassDescriptor)
else { fatalError() }
```

Here’s what’s happening:

1. You create a command buffer. This stores all the commands that you’ll ask the GPU to run.

2. You obtain a reference to the view’s render pass descriptor. The descriptor holds data for the render destinations, known as attachments. Each attachment needs information, such as a texture to store to, and whether to keep the texture throughout the render pass. The render pass descriptor is used to create the render command encoder.

3. From the command buffer, you get a render command encoder using the render pass descriptor. The render command encoder holds commands that the GPU will execute, providing all the information necessary for the GPU to render the frame.

<a id="page-41"></a>

If the system fails to create a Metal object, such as the command buffer or render encoder, that’s a fatal error. The view’s currentRenderPassDescriptor may not be available in a particular frame, and usually you’ll just return from the rendering delegate method. Because you’re asking for it only once in this playground, you get a fatal error.

➤ Add the following code:

`renderEncoder.setRenderPipelineState(pipelineState)`

This code gives the render encoder the pipeline state that you set up earlier.

The sphere mesh that you loaded earlier holds a buffer containing a simple list of vertices.

➤ Give this buffer to the render encoder by adding the following code:

```
renderEncoder.setVertexBuffer(
  mesh.vertexBuffers[0].buffer, offset: 0, index: 0)
```

The offset is the position in the buffer where the vertex information starts. The index is how the GPU vertex shader function locates this buffer.

## **Submeshes**

The mesh is made up of submeshes. When artists create 3D models, they design them with different material groups. These translate to submeshes. For example, if you were rendering a car object, you might have a shiny car body and rubber tires. One material is shiny paint and another is rubber. On import, Model I/O creates two different submeshes that index to the correct vertices for that group. One vertex can be rendered multiple times by different submeshes. This sphere only has one submesh, so you’ll use only one.

➤ Add this code:

```
guard let submesh = mesh.submeshes.first else {
  fatalError()
}
```

Now for the exciting part: drawing! You draw in Metal with a draw call.

<a id="page-42"></a>

➤ Add this code:

```
renderEncoder.drawIndexedPrimitives(
  type: .triangle,
  indexCount: submesh.indexCount,
  indexType: submesh.indexType,
  indexBuffer: submesh.indexBuffer.buffer,
  indexBufferOffset: 0)
```

Here, you instruct the GPU to render a vertex buffer consisting of triangles with the vertices placed in the correct order by the submesh index information. This code doesn’t do the actual render — that doesn’t happen until the GPU has received all the command buffer’s commands. You are merely adding to the list of commands that the GPU will eventually execute.

➤ To complete sending commands to the render command encoder and finalize the frame, add this code:

```
// 1
renderEncoder.endEncoding()
// 2
guard let drawable = view.currentDrawable else {
  fatalError()
}
// 3
commandBuffer.present(drawable)
commandBuffer.commit()
```

Going through the code:

1. You tell the render encoder there are no more draw calls and end the render pass.

2. You get the drawable from the MTKView. The MTKView is backed by a Core Animation CAMetalLayer and the layer owns a drawable texture which Metal can read and write to.

3. You ask the command buffer to present the MTKView’s drawable and commit to the GPU.

<a id="page-43"></a>

➤ Run the playground, and in the playground’s live view, you’ll see a red sphere on a cream background.

![Figure](Metal_by_Tutorials_v500mpdf/4d187dc915b96a1aa270319e.png)

Note: Sometimes playgrounds don’t compile or run when they should. If you’re sure you’ve written the code correctly, then restart Xcode and reload the playground. Wait for a second or two before running.

Congratulations! You’ve written your first Metal app, and you’ve also used many of the Metal API commands that you’ll use in every Metal app you write.

![Figure](Metal_by_Tutorials_v500mpdf/3cf5f8f50b9d31b3db782768.png)

<a id="page-44"></a>

## **Challenge**

Where you created the initial sphere mesh, experiment with setting the sphere to different sizes. For example, change the size from:

`[0.75, 0.75, 0.75]`

To:

`[0.2, 0.75, 0.2]`

Change the color of the sphere. In the shader function string, you’ll see:

`return float4(1, 0, 0, 1);`

This code returns red=1, green=0, blue=0, alpha=1, which results in the red color. Try changing the numbers (from zero to 1) for a different color. Try this green, for example:

`return float4(0, 0.4, 0.21, 1);`

In the next chapter, you’ll examine 3D models up close in Blender. Then continuing in your Swift Playground, you’ll import and render a train model.

<a id="page-45"></a>

## **Key Points**

• Rendering means to create a 2D image from three-dimensional points.

• A frame is an image that the GPU renders sixty times a second (optimally).

• device is a software abstraction for the hardware GPU.

• A 3D model consists of a vertex mesh with shading materials grouped in submeshes.

• Create a command queue at the start of your app. This action organizes the command buffer and command encoders that you’ll create every frame.

• Shader functions are programs that run on the GPU. You position vertices and color the pixels in these programs.

• The render pipeline state fixes the GPU into a particular state. It can set which shader functions the GPU should run and how vertex layouts are formatted.

Learning computer graphics is difficult. The Metal API is modern, and it takes a lot of pain out of the learning, but you need to know a lot of information up-front. Even if you feel overwhelmed at the moment, continue with the next chapters. Repetition will help with your understanding.

<a id="page-46"></a>

# 2

# Chapter 2: 3D Models

Do you know what makes a good game even better? Gorgeous graphics!

Creating amazing graphics such as those in Baldur’s Gate 3, Crimson Desert and Cyberpunk 2077, generally requires a skilled team of programmers and 3D artists. The graphics you see onscreen are created using 3D models that are rendered with custom renderers, similar to the one you wrote in the previous chapter, only more advanced. Nevertheless, the principle of rendering 3D models is still the same.

In this chapter, you’ll learn all about 3D models, including how to render them onscreen, and how to work with them in Blender.

<a id="page-47"></a>

## **What Are 3D Models?**

3D models are made up of vertices. Each vertex refers to a point in 3D space using x, y and z values.

![Figure](Metal_by_Tutorials_v500mpdf/2877bb36d393570c415e085f.png)

_A vertex in 3D space._

As you saw in the previous chapter, you send these vertex points to the GPU for rendering. You need three vertices to create a triangle, and GPUs are able to render triangles efficiently. To show smaller details, a 3D model may also use textures. You’ll learn more about textures in Chapter 8, “Textures”.

➤ Open the starter playground for this chapter.

This playground contains two pages named 1 Render and Export 3D Model and 2 Import Train, as well as the train model in USDZ format. If you don’t see these items, you may need to hide/show the Project navigator using the icon at the top-left.

![Figure](Metal_by_Tutorials_v500mpdf/548522aa1348a3beb4a62512.png)

_The Project Navigator_

<a id="page-48"></a>

To show the file extensions, open Xcode Settings, and on the General tab, choose File Extensions: Show All.

![Figure](Metal_by_Tutorials_v500mpdf/a75fa1d9c7c29bbc5cd4c252.png)

_Show File Extensions_

➤ From the Project navigator, select 1 Render and Export 3D Model.

This page contains the final code from Chapter 1, “Hello, Metal!”.  Examine the rendered sphere in the playground’s live view. Notice how the sphere renders as a solid red shape and appears flat.

To see the edges of each individual triangle, you can render the model in wireframe.

➤ To render in wireframe, add the following code just after renderEncoder.setVertexBuffer(...):

`renderEncoder.setTriangleFillMode(.lines)`

This code tells the GPU to render lines instead of solid triangles.

<a id="page-49"></a>

➤ Run the playground:

![Figure](Metal_by_Tutorials_v500mpdf/3bbd11eb74d85424b58cb8ef.png)

_A sphere rendered in wireframe._

There’s a bit of an optical illusion happening here. It may not look like it, but the GPU is rendering straight lines. The reason the sphere edges look curved is because of the number of triangles the GPU is rendering. You specified [30, 30] segments when you generated the sphere. If you render fewer triangles, curved models tend to look “blocky”.

You can really see the 3D nature of the sphere now. The model’s triangles are evenly spaced horizontally, but because you’re viewing on a two dimensional screen, they appear smaller at the edges of the sphere than the triangles in the middle.

<a id="page-50"></a>

In 3D apps such as Blender or Maya, you generally manipulate points, lines and faces. Points are the vertices; lines, also called edges, are the lines between the vertices; and faces are the triangular flat areas.

![Figure](Metal_by_Tutorials_v500mpdf/aa206dc46244097f1ba666f4.png)

_Vertex, line and face._

The vertices are generally ordered into triangles because GPU hardware is specialized to process them. The GPU’s core instructions are expecting to see a triangle. Of all possible shapes, why a triangle?

• A triangle has the least number of points of any polygon that can be drawn in two dimensions.

• No matter which way you move the points of a triangle, the three points will always be on the same plane.

• When you divide a triangle starting from any vertex, it always becomes two triangles.

When you’re modeling in a 3D app, you generally work with quads (four point polygons). Quads work well with subdivision or smoothing algorithms. When you import the model using the Model I/O framework, Model I/O converts these quads to triangles.

<a id="page-51"></a>

## **Creating Models With Blender**

To create 3D models, you need a 3D modeling app. These apps range from free to hugely expensive. The best of the free apps — and the one used throughout this book — is Blender (v. 4.5). A lot of professionals use Blender, but if you’re more familiar with another 3D app, such as Cheetah3D, Maya or Houdini, then you’re welcome to use it since the concepts are the same.

➤ Download and install Blender from https://www.blender.org.

➤ Launch Blender. Click outside of the splash screen to close it, and you’ll see an interface similar to this one:

![Figure](Metal_by_Tutorials_v500mpdf/1febb2e7a67a66969828a4a4.png)

_The Blender Interface._

Your interface may look different. However, if you want your Blender interface to look like the image shown here, choose Edit ▸ Preferences…. Click the hamburger menu at the bottom left, choose Load Factory Preferences, and then click the pop-up Load. Click Save Preferences to retain these preferences for future sessions.

<a id="page-52"></a>

Note: If you want to create your own models, the best place to start is with our Blender tutorial (https://bit.ly/3gwKiel). This tutorial teaches you how to make a mushroom. You can then render your mushroom in your playground at the end of this chapter.

![Figure](Metal_by_Tutorials_v500mpdf/48bcbf2495a955ea7e0df9aa.png)

_A mushroom modeled in Blender._

## **3D File Formats**

There are several standard 3D file formats. Here’s an overview of what each one offers:

• OBJ: This format, developed by Wavefront Technologies, has been around for a long time, and almost every 3D app supports importing and exporting OBJ files with the .obj extension. You can specify materials (textures and surface properties) using an accompanying .mtl file, however, this format does not support animation.

• glTF: The GL Transmission Format was developed by Khronos, who oversee Vulkan and OpenGL. This format is relatively new and is still under active development. It has strong community support because of its flexibility. It supports animated models.

• .blend: This is the native Blender file format.

<a id="page-53"></a>

• .fbx: A proprietary format owned by Autodesk. This is a commonly used format that supports animation but is losing favor because it’s proprietary and doesn’t have a single standard.

• USD: Universal Scene Description is a scalable open source format introduced by Pixar, with full documentation at https://openusd.org. A USD file can reference many models and files, so each person on a team can work on a separate part of the scene. A USD file can have several different extensions. .usd can be either ASCII or binary. .usda is human-readable ASCII. .usdz is a USD archive file that contains everything needed for the model or scene. Apple uses the USDZ format for their AR models. You can download examples from Apple’s AR gallery (https:// apple.co/3iJzMBW).

An OBJ file contains only a single model, whereas glTF and USD files are containers for entire scenes, complete with models, animation, cameras and lights.

In this book, you’ll mainly use the USD format.

## **Exporting to Blender**

Now that you have Blender all set up, it’s time to export a model from your playground into Blender.

➤ Still in 1 Render and Export 3D Model, near the top of the playground where you create the mesh, change:

```
let mdlMesh = MDLMesh(
  sphereWithExtent: [0.75, 0.75, 0.75],
  segments: [30, 30],
  inwardNormals: false,
  geometryType: .triangles,
  allocator: allocator)
```

To:

```
let mdlMesh = MDLMesh(
  coneWithExtent: [1, 1, 1],
  segments: [10, 10],
  inwardNormals: false,
  cap: true,
  geometryType: .triangles,
  allocator: allocator)
```

<a id="page-54"></a>

This code will generate a primitive cone mesh in place of the sphere. Run the playground, and you’ll see the wireframe cone.

![Figure](Metal_by_Tutorials_v500mpdf/69be569176aab10956605760.png)

_A cone model._

This is the model you’ll export using Model I/O.

➤ Open Finder, and in the Documents folder, create a new directory named Shared Playground Data. All your saved files from the Playground will end up here, so make sure you name it correctly.

Note: The global constant playgroundSharedDataDirectory holds this folder name.

➤ To export the cone, add this code just after creating the mesh:

```
// begin export code
// 1
let asset = MDLAsset()
asset.add(mdlMesh)
// 2
let fileExtension = "usda"
guard MDLAsset.canExportFileExtension(fileExtension) else {
  fatalError("Can't export a .\(fileExtension) format")
}
// 3
do {
  let url = playgroundSharedDataDirectory
    .appendingPathComponent("generatedCone.\(fileExtension)")
  try asset.export(to: url)
} catch {
```

<a id="page-55"></a>

```
  fatalError("Error \(error.localizedDescription)")
}
// end export code
```

Let’s have a closer look at the code:

1. The top level of a scene in Model I/O is an MDLAsset. You can build a complete scene hierarchy by adding child objects such as meshes, cameras and lights to the asset.

2. Check that Model I/O can export a .usda file type. You would generally choose .usd or .usdz, but choosing the ASCII text format here will allow you examine the contents of the file.

3. Export the cone to the directory stored in Shared Playground Data.

➤ Run the playground to export the cone object.

Note: If your playground crashes, it’s probably because you haven’t created the Shared Playground Data directory in Documents.

## **The USD File Format**

➤ In Finder, navigate to Documents ▸ Shared Playground Data.

Here, you’ll find the exported file, generatedCone.usda.

➤ Using a plain text editor, open generatedCone.usda.

The following is an example USD file that describes a plane primitive with four corner vertices. The cone USD file looks similar, except it has more vertex data.

```
#usda 1.0
(
  defaultPrim = "generatedPlane"
  upAxis = "Y"
)
def Xform "generatedPlane" (...)
{
  def Scope "Geom"
  {
    def Mesh "plane" (...)
    {
      float3[] extent = [(-0.5, 0, -0.5), (0.5, 0, 0.5)]
```

<a id="page-56"></a>

```
      int[] faceVertexCounts = [3, 3]
      int[] faceVertexIndices = [3, 2, 1, 3, 1, 0]
      rel material:binding = </generatedPlane/Materials/
plane_Material>
      normal3f[] normals = [(0, 1, 0), (0, 1, 0), (0, 1, 0) ...
      point3f[] points = [(0.5, 0, 0.5), (-0.5, 0, 0.5),
(-0.5, ...
      float2[] primvars:st = [(1, 1), (0, 1), (0, 0), (1, 0)] (
         interpolation = "vertex"
      )
      uniform token subdivisionScheme = "none"
    }
  }
  def Scope "Materials"
  {
    def Material "plane_Material"
    ...
}
```

The file starts with describing the general features, such as animation timing, if there is any, and which way is up. The file then describes the mesh geometry.

Here’s the breakdown of the plane USD:

• extent: the size of the mesh. When creating your cone, in coneWithExtent you specified 1 on all axes. The minimum vertex position value will be -0.5 and the maximum will be 0.5.

• faceVertexCounts: This plane consists of two triangles with three vertices each. Your cone will have many triangles.

• faceVertexIndices: This plane has four vertices, one at each corner. The index order is the order these vertices are rendered. To make up two triangles, you render six vertices.

• rel material:binding: A link to the material described later in the file for shading.

<a id="page-57"></a>

• normals: The surface normals. A normal is a vector that points orthogonally — that’s directly outwards. You’ll read more about normals later.

• points: The position of each vertex. The plane has four vertices. Your cone will have many vertices.

• primvars:st: These are the texture coordinates that determines a vertex’s position on a 2D texture. Coordinates on textures are called uv coordinates rather than xy coordinates, but they work the same. uv coordinates map into st texture space. Your cone doesn’t use these UV coordinates because you haven’t applied any custom textures to it.

## **Importing the Cone**

It’s time to import the cone into Blender.

➤ To start with a clean and empty Blender file:

1. Open Blender.

2. Choose File ▸ New ▸ General.

3. Left-click the cube that appears in the start-up file to select it.

4. Press X to delete the cube.

5. Left-click Delete in the menu under the cursor to confirm the deletion.

You now have a clear and ready-for-importing Blender file, so let’s get to it.

➤ Choose File ▸ Import ▸ Universal Scene Description (.usd\*), and select generatedCone.usda from the Documents ▸ Shared Playground Data Playground directory.

<a id="page-58"></a>

➤ On the right of the import panel, change the Scale to 100 and click Import USD.

![Figure](Metal_by_Tutorials_v500mpdf/91afce73d63e3ac292221796.png)

_Import the cone._

The cone imports into Blender.

![Figure](Metal_by_Tutorials_v500mpdf/0b5c152fb47bfedd4f17301a.png)

_The cone in Blender._

<a id="page-59"></a>

You can zoom and pan using the navigation controls at the top right of the pane.

![Figure](Metal_by_Tutorials_v500mpdf/181cfb391b6cf93649f34d9b.png)

_Blender navigation._

➤ Left-click the cone to select it, and press Tab to put Blender into Edit Mode. Edit Mode allows you to see the vertices and triangles that make up the cone. These match your wireframe render.

![Figure](Metal_by_Tutorials_v500mpdf/738ad558c280632b819324b4.png)

_Edit mode_

While you’re in Edit Mode, you can move the vertices around and add new vertices to create any 3D model you can imagine.

Using only a playground, you now have the ability to create, render and export a primitive. In the next part of this chapter, you’ll review and render a more complex model with separate material groups.

<a id="page-60"></a>

## **Materials**

Materials describe how the 3D renderer should color a vertex. For example, should the vertex be smooth and shiny? Pink? Reflective?

Material properties can include:

• diffuse: The basic color of the surface.

• metallic: Describes whether the surface is a metal.

• roughness: Describes how rough a surface is. If the surface has a roughness of 0, it is completely flat and shiny.

## **Material Groups**

➤ In Blender, open train.blend, which you’ll find in the resources directory for this chapter.

This file is the original Blender file of the .usdz train in your playground.

➤ **Left-click the model** to select it, and press **Tab** to go into Edit Mode.

![Figure](Metal_by_Tutorials_v500mpdf/118857c7ab81d8c3e88f1340.png)

_The train in edit mode._

Unlike the cone, which is plain gray, the train model has several colors. These colors are defined in material groups — one for each color. On the right-hand side of the Blender screen, you’ll see the Properties panel, with the Material context already selected (that’s the icon at the bottom of the vertical list of icons), and the list of materials within this model at the top.

<a id="page-61"></a>

➤ Select **Body**, and then click **Select** underneath the material list.

The vertices assigned to this material are now colored orange.

![Figure](Metal_by_Tutorials_v500mpdf/356bb8b6f90802e8110fc109.png)

_Material groups_

Notice how the vertices are separated into different groups or materials. This separation makes it easier to select the various parts within Blender and also gives you the ability to assign different colors.

Note: When you render this model into your playground, the renderer will render each of the material groups, but your Metal shader will not yet render the correct colors. One way to verify a model’s appearance is to view it in Blender.

➤ Go back to Xcode, and from the Project navigator, open the 2 Import Train playground page. This playground renders — but does not export — the wireframe cone.

➤ In the playground’s Resources folder, find and examine the train.usdz model. Drag on the window to move the view camera around the model.

Note: Files in the Playground Resources folder are available to all playground pages. Files in each page’s Resources folder are only available to that page.

<a id="page-62"></a>

➤ In **2 Import Train**, remove the lines where you create the `MDLMesh` cone:

```
let mdlMesh = MDLMesh(
  coneWithExtent: [1, 1, 1],
  segments: [10, 10],
  inwardNormals: false,
  cap: true,
  geometryType: .triangles,
  allocator: allocator)
```

Don’t worry about that compile error. You’ve still got some work to do.

➤ Replacing the code you just removed, add this code in its place:

```
guard let assetURL = Bundle.main.url(
  forResource: "train",
  withExtension: "usdz") else {
  fatalError()
}
```

This code sets up the URL for the USD file.

## **Vertex Descriptors**

Metal uses descriptors as a common pattern to create objects. You saw this pattern in the previous chapter when you set up a pipeline descriptor to describe a pipeline state. Before loading the model, you’ll tell Metal how to lay out the vertices and other data by creating a vertex descriptor.

The following diagram describes an incoming buffer of model vertex data. It has two vertices with position, normal and texture coordinate attributes. The vertex descriptor informs Metal how you want to view this data.

![Figure](Metal_by_Tutorials_v500mpdf/d94be83f878432001cd7dd9f.png)

_The vertex descriptor_

<a id="page-63"></a>

➤ Add the following code below the code you just added:

```
// 1
let vertexDescriptor = MTLVertexDescriptor()
// 2
vertexDescriptor.attributes[0].format = .float3
// 3
vertexDescriptor.attributes[0].offset = 0
// 4
vertexDescriptor.attributes[0].bufferIndex = 0
```

Looking closer:

1. You create a vertex descriptor that you’ll use to configure all of the properties that an object will need to know about.

Note: You can reuse this vertex descriptor with either the same values or reconfigured values to instantiate a different model object.

2. The USD file holds normal and texture coordinate data as well as vertex position data. For the moment, you don’t need the surface normals or texture coordinates; you only need the position. You tell the descriptor that the xyz position data should load as a float3, which is a SIMD data type consisting of three Float values. An MTLVertexDescriptor has an array of 31 attributes where you can configure the data format. In later chapters, you’ll load the normal and texture coordinate attributes.

3. The offset specifies where in the buffer this particular data will start.

4. When you send your vertex data to the GPU via the render encoder, you send it in an MTLBuffer and bind the buffer to an index. There are 31 buffers available. Metal keeps track of these buffer bindings in a buffer argument table. You use buffer 0 here so that the vertex shader function will be able to match the incoming vertex data in buffer 0 with this vertex layout.

<a id="page-64"></a>

➤ Now add this code below the previous lines:

```
// 1
vertexDescriptor.layouts[0].stride =
  MemoryLayout<SIMD3<Float>>.stride
// 2
let meshDescriptor =
  MTKModelIOVertexDescriptorFromMetal(vertexDescriptor)
// 3
(meshDescriptor.attributes[0] as! MDLVertexAttribute).name =
  MDLVertexAttributePosition
```

Going through everything:

1. Here, you specify the stride for buffer 0. The stride is the number of bytes between each set of vertex information. Referring back to the previous diagram which described position, normal and texture coordinate information, the stride between each vertex would be float3 + float3 + float2. However, here you’re only loading position data, so to get to the next position, you jump by a stride of float3. The SIMD3&lt;Float&gt; type is Swift’s equivalent to float3. Later, you’ll use a typealias for float3.

Using the buffer layout index and stride format, you can set up complex vertex descriptors referencing multiple MTLBuffers with different layouts. You have the option of interleaving position, normal and texture coordinates; or you can lay out a buffer containing all of the position data first, followed by other data.

2. Model I/O needs a slightly different format vertex descriptor, so you create a new Model I/O descriptor from the Metal vertex descriptor. If you have a Model I/O descriptor and need a Metal one, MTKMetalVertexDescriptorFromModelIO() provides a solution.

3. Assign a string name “position” to the attribute. This tells Model I/O that this is positional data. The normal and texture coordinate data is also available, but with this vertex descriptor, you told Model I/O that you’re not interested in loading those attributes.

<a id="page-65"></a>

➤ Continue by adding this code:

```
let asset = MDLAsset(
  url: assetURL,
  vertexDescriptor: meshDescriptor,
  bufferAllocator: allocator)
let mdlMesh =
  asset.childObjects(of: MDLMesh.self).first as! MDLMesh
```

This code reads the asset using the URL, vertex descriptor and memory allocator. You then read in the first Model I/O mesh buffer in the asset. Some more complex objects will have multiple meshes, but you’ll deal with that later.

Now that you’ve loaded the model vertex information, the rest of the code will be the same, and your playground will load mesh from the new mdlMesh variable.

➤ Run the playground to see your train in wireframe.

![Figure](Metal_by_Tutorials_v500mpdf/79f5e9f42a0936a7cd69c1d9.png)

_Train wireframe wheels_

Well, that’s not good. The train wheels are way too high off the ground. Plus, the rest of the train is missing! Time to fix these problems, starting with the train’s wheels.

<a id="page-66"></a>

## **Metal Coordinate System**

All models have an origin. The origin is the location of the mesh. The train’s origin is at [0, 0, 0]. In Blender, this places the train right at the center of the scene.

![Figure](Metal_by_Tutorials_v500mpdf/1c36a576a56b0ee73e59b12c.png)

_The origin_

The Metal NDC (Normalized Device Coordinate) system is a 2-unit wide by 2-unit high by 1-unit deep box where X is right / left, Y is up / down and Z is in / out of the screen.

![Figure](Metal_by_Tutorials_v500mpdf/b9e33ce95400a1d3376ece23.png)

_NDC (Normalized Device Coordinate) system_

<a id="page-67"></a>

To normalize means to adjust to a standard scale. On a screen, you might address a location in screen coordinates of width 0 to 375, whereas the Metal normalized coordinate system doesn’t care what the physical width of a screen is — its coordinates along the X axis are -1.0 to 1.0. In Chapter 6, “Coordinate Spaces”, you’ll learn about various coordinate systems and spaces. Because the origin of the train is at [0,0,0], the train appears halfway up the screen, which is where [0,0,0] is in the Metal coordinate system.

The GPU renders the vertex position according the output of the vertex function. Your playground currently contains a very simple vertex function, which returns the vertex position handed to it.

➤ In your playground, locate `let shaders = """..."""`

shaders is a text string that contains the shader function code that the Metal library loads and compiles. By changing vertex\_in.position in this string, you can change the render position of each vertex.

Within the `shaders` text string, change `return vertex_in.position;` to:

```
float4 position = vertex_in.position;
position.y -= 1.0;
return position;
```

Be careful to add this code exactly as shown, including the ; at the end of each line. Because the code is contained in a string, the compiler can’t recognize errors.

Here, you subtract 1.0 from the y position of every vertex rendered. NDC’s -1.0 in the y axis is at the bottom of the screen. Don’t worry if you don’t quite understand what’s happening yet, as you’ll revisit this topic in Chapter 4, “The Vertex Function”.

➤ Run the playground. The wheels now appear at the bottom of the screen.

![Figure](Metal_by_Tutorials_v500mpdf/0adf409e04bd4300bac42da3.png)

_Wheels on the ground_

Now that the wheels are fixed, you’re ready to solve the case of the missing train!

<a id="page-68"></a>

## **Submeshes**

So far, your primitive sphere and cone models included only one material group, and thus one submesh. Here’s a plane with four vertices and two material groups.

![Figure](Metal_by_Tutorials_v500mpdf/82362a4822f9dc279e000fb4.png)

_Vertices on a plane_

When Model I/O loads this plane, it places the four vertices in an MTLBuffer. The following image shows the vertex position data and also how two submesh buffers index into the vertex data.

![Figure](Metal_by_Tutorials_v500mpdf/e9874cd1f849ca0b93f8e360.png)

_Submesh buffers_

The first submesh buffer holds the vertex indices of the light-colored triangle ACD. These indices point to vertices 0, 2 and 3 (ACD). The second submesh buffer holds the indices of the dark triangle ADB. Each submesh also has an offset where the submesh buffer starts. The second submesh’s offset is 3, as the submesh starts at the fourth index.

<a id="page-69"></a>

## **Winding Order**

The vertex order, also known as the winding order, is important here. The vertex order of this plane is counter-clockwise. With a counter-clockwise winding order, triangles that are defined in counter-clockwise order are facing toward you. Whereas triangles that are in clockwise order are facing away from you. In the next chapter, you’ll go down the graphics pipeline and you’ll see that the GPU can cull triangles that are not facing toward you, saving valuable processing time.

## **Render Submeshes**

Currently, you’re only rendering the first submesh, but because the train has several material groups, you’ll need to loop through the submeshes to render them all.

➤ Toward the end of the playground, change:

```
guard let submesh = mesh.submeshes.first else {
 fatalError()
}
renderEncoder.drawIndexedPrimitives(
  type: .triangle,
  indexCount: submesh.indexCount,
  indexType: submesh.indexType,
  indexBuffer: submesh.indexBuffer.buffer,
  indexBufferOffset: 0)
```

To:

```
for submesh in mesh.submeshes {
  renderEncoder.drawIndexedPrimitives(
    type: .triangle,
    indexCount: submesh.indexCount,
    indexType: submesh.indexType,
    indexBuffer: submesh.indexBuffer.buffer,
    indexBufferOffset: submesh.indexBuffer.offset
  )
}
```

This code loops through the submeshes and issues a draw call for each one. The mesh and submeshes are in MTLBuffers, and the submesh holds the index listing of the vertices in the mesh.

<a id="page-70"></a>

➤ Run the playground, and your train renders completely — minus the material colors, which you’ll take care of in Chapter 11, “Maps &amp; Materials”.

![Figure](Metal_by_Tutorials_v500mpdf/e6129c81bd94132d4901ae90.png)

_The final train_

Congratulations! You’re now rendering 3D models. For now, don’t worry that you’re only rendering them in two dimensions or that the colors aren’t correct. After the next chapter, you’ll know more about the internals of rendering. Following on from that, you’ll learn how to move those vertices into the third dimension.

<a id="page-71"></a>

## **Challenge**

If you’re in for a fun challenge, complete the Blender tutorial to make a mushroom (https://www.kodeco.com/21459096-blender-tutorial-for-beginners-how-to-make-a-mushroom), and then export what you make in Blender to a .usdz file. If you want to skip the modeling, you’ll find the mushroom.usdz file in the resources directory for this chapter.

➤ Import **mushroom.usdz** into the playground and render it.

If you use your own modeled mushroom, you may find that the mushroom is lying on its side. Blender uses the Z axis as up, whereas your playground is expecting the Y axis as up. Before exporting to USD, you should rotate the model by 180º on the Z axis and 270º on the X axis. You must then apply all the transforms in Blender before exporting using menu option Object ▸ Apply ▸ All Transforms. mushroom.usdz in the resources directory has already been rotated.

![Figure](Metal_by_Tutorials_v500mpdf/b97890ee43d095092d06f36a.png)

_Wireframe mushroom_

If you have difficulty, the completed playground is in the challenge directory for this chapter.

<a id="page-72"></a>

## **Key Points**

• 3D models consist of vertices. Each vertex has a position in 3D space.

• In 3D modeling apps, you create models using quads, or polygons with four vertices. On import, Model I/O converts these quads to triangles.

• Triangles are the GPU’s native format.

• There are many 3D file formats. Apple has standardized its AR models on Pixar’s USD format in a compressed USDZ format.

• Vertex descriptors describe the buffer format for the model’s vertices. You set the GPU pipeline state with the vertex descriptor, so that the GPU knows what the vertex buffer format is.

• You bind resources to the GPU’s argument table using indices. Shader functions reference these resources using attributes and the same indices.

• A model is made up of at least one submesh. This submesh corresponds to a material group where you can define the color and other surface attributes of the group.

• Metal Normalized Device Coordinates are -1 to 1 on the X and Y axes, and 0 to 1 on the Z axis. X is left / right, Y is down / up and Z is front / back.

• The GPU will render only vertices positioned in Metal NDC.

<a id="page-73"></a>

# 3

# Chapter 3: The Rendering Pipeline

Now that you know a bit more about 3D models and rendering, it’s time to take a drive through the rendering pipeline. In this chapter, you’ll create a Metal app that renders a red cube. As you work your way through this chapter, you’ll get a closer look at the hardware that’s responsible for turning your 3D objects into the gorgeous pixels you see onscreen.

Unlike previous generations of hardware, where the GPU was on a discrete swappable board, Apple Silicon is a System on a Chip (SoC). This means that the Central Processing Unit (CPU) and Graphics Processing Unit (GPU), as well as the Neural Engine and memory are all on one single chip. Having all the components on one chip, brings many benefits. Each component is physically closer, which means that transfer of data is faster and more efficient.

<a id="page-74"></a>

Apple doesn’t share the designs of their chips, but they provide high level diagrams such as the following one:

![Figure](Metal_by_Tutorials_v500mpdf/c784646b9e4b0753d02e0348.png)

_Apple's M4 chip_

M4 when first released in iPad Pro, had a ten-core CPU and a ten-core GPU. These might be the same numbers, but each component processes differently.

## **The GPU and CPU**

The GPU is a specialized hardware component that can process images, videos and massive amounts of data really fast. This operation is known as throughput and is measured by the amount of data processed in a specific unit of time. The CPU, on the other hand, manages resources and is responsible for the computer’s operations. Although the CPU can’t process huge amounts of data like the GPU, it can process many sequential tasks (one after another) really fast. The time necessary to process a task is known as latency.

The ideal setup includes low latency and high throughput. Low latency allows for the serial execution of queued tasks, so the CPU can execute the commands without the system becoming slow or unresponsive — and high throughput lets the GPU render videos and games asynchronously without stalling the CPU. Because the GPU has a highly parallelized architecture specialized in doing the same task repeatedly and with little or no data transfers, it can process larger amounts of data.

<a id="page-75"></a>

To visualize this, if you are placing colored pixels into a texture, the CPU would place them one at a time, sequentially:

![Figure](Metal_by_Tutorials_v500mpdf/20e304c6ad849339555e808d.png)

_CPU processing_

The GPU would take longer to set up the placement, but would then perform the operation all at once in parallel:

![Figure](Metal_by_Tutorials_v500mpdf/ebb7106cde673dfedb792324.png)

_GPU processing_

You can see that if you are doing the same operation on many items, the GPU is well-suited to the task.

It’s time for you to walk through the graphics pipeline in a project. You’ll first set up the GPU commands and resources on the CPU, then discover how to handle the GPU.

## **The Metal Project**

So far, you’ve been using Playgrounds to learn about Metal. Playgrounds are great for testing and learning new concepts, but it’s also important to understand how to set up a full Metal project using SwiftUI.

➤ In Xcode, create a new project using the **Multiplatform App** template.

➤ Name your project Pipeline, and fill out your team and organization identifier. Set the Testing System and Storage settings to None.

<a id="page-76"></a>

➤ Choose the location for your new project.

Excellent, you now have a fancy, new SwiftUI app. ContentView.swift is the main view for the app; this is where you’ll call your Metal view.

The MetalKit framework contains an MTKView, which is a special Metal rendering view. This is a UIView on iOS and an NSView on macOS. To interface with UIKit or Cocoa UI elements, you’ll use a Representable protocol that sits between SwiftUI and your MTKView.

This configuration is a bit complicated, so in the resources folder for this chapter, you’ll find a pre-made MetalView.swift.

➤ Drag this file into your project, making sure that you choose to copy the file and add it to the app’s target.

![Figure](Metal_by_Tutorials_v500mpdf/ef66c72a9a1716dd48198628.png)

_Adding the file to the project_

➤ Open MetalView.swift.

MetalView is the View interface, hosting either the UIView or the NSView, depending on the operating system. When you create the view, MetalView instantiates a Renderer class. You’ll replace this Renderer with your own class shortly.

➤ Open **ContentView.swift**, and change the contents of `body` to:

```
VStack {
  MetalView()
    .border(Color.black, width: 2)
  Text("Hello, Metal!")
}
.padding()
```

<a id="page-77"></a>

Here, you add `MetalView` to the view hierarchy and give it a border.

➤ Build and run your app, choosing **My Mac** as the destination.

Note: If you are not developing on Apple Silicon, you should still be able to follow along by running the app on a recent device.

You’ll see your hosted MTKView. The advantage of using SwiftUI is that it’s relatively easy to layer UI elements — such as the “Hello Metal” text here — below your Metal view. You can easily layer your app’s user interface over the MTKView.

![Figure](Metal_by_Tutorials_v500mpdf/1cfca82b9ece3abbfe7057d0.png)

_Initial SwiftUI View_

You now have a choice. You can subclass MTKView and replace the MTKView in MetalView with the subclassed one. In this case, the subclass’s draw(\_:) would get called every frame, and you’d put your drawing code in that method. However, in this book, you’ll set up a Renderer class that conforms to MTKViewDelegate and sets Renderer as a delegate of MTKView. MTKView calls a delegate method every frame, and this is where you’ll place the necessary drawing code.

Note: If you’re coming from a different API world, you might be looking for a game loop construct. You do have the option of using CAMetalDisplayLink for more control over timing, but Apple introduced MetalKit with its protocols to manage the game loop more easily.

<a id="page-78"></a>

## **The Renderer Class**

➤ First, remove the three-line Renderer class from MetalView.swift. This will give a compile error until you create your own Renderer.

➤ Create a new Swift file named Renderer.swift, and replace its contents with the following code:

```
import MetalKit

class Renderer: NSObject {
  init(metalView: MTKView) {
    super.init()
  }
}

extension Renderer: MTKViewDelegate {
  func mtkView(
    _ view: MTKView,
    drawableSizeWillChange size: CGSize
  ) {
  }

  func draw(in view: MTKView) {
    print("draw")
  }
}
```

Here, you create an initializer and make Renderer conform to MTKViewDelegate with the two MTKView delegate methods:

• mtkView(\_:drawableSizeWillChange:): Called every time the size of the window changes. This allows you to update render texture sizes and camera projection.

• draw(in:): Called every frame. This is where you write your render code. Until you have something to render, use the print statement to verify that your app is calling draw(in:) for every frame.

<a id="page-79"></a>

## **Initialization**

Just as you did in the first chapter, you need to set up the Metal environment. You should instantiate as many objects as you can up-front rather than create them during every frame. The following diagram indicates some of the Metal objects you can create at the start of the app.

![Figure](Metal_by_Tutorials_v500mpdf/e7a40b220d84275226891cc8.png)

_Create these outside the render loop_

• MTLDevice: The software reference to the GPU hardware device.

• MTLCommandQueue: Responsible for creating and organizing MTLCommandBuffers every frame.

• MTLLibrary: Contains the source code from your vertex and fragment shader functions.

• MTLRenderPipelineState: Sets the information for the draw — such as which shader functions to use, what depth and color settings to use and how to read the vertex data.

• MTLBuffer: Holds data — such as vertex information — in a form that you can send to the GPU.

• MTLTexture: Holds image data in a specified pixel format.

Typically, you’ll have one MTLDevice, one MTLCommandQueue and one MTLLibrary object in your app. You’ll have several MTLRenderPipelineState objects that will define different ways of shading or doing compute operations, such as particle effects or ray tracing. You’ll have many MTLBuffers to hold vertex data and MTLTextures for texturing your models.

Before you can use these objects, you need to initialize them.

<a id="page-80"></a>

➤ Open Renderer.swift, and add these properties to Renderer:

```
static var device: MTLDevice!
static var commandQueue: MTLCommandQueue!
static var library: MTLLibrary!
var mesh: MTKMesh!
var vertexBuffer: MTLBuffer!
var pipelineState: MTLRenderPipelineState!
```

All of these properties are currently implicitly unwrapped optionals for convenience, but you can add error-checking later if you wish.

You’re using class properties for the device, the command queue and the library to ensure that only one of each exists. In rare cases, you may require more than one, but in most apps, one is enough.

➤ Still in Renderer.swift, add the following code to init(metalView:) before super.init():

```
guard
  let device = MTLCreateSystemDefaultDevice(),
  let commandQueue = device.makeCommandQueue() else {
    fatalError("GPU not available")
}
Self.device = device
Self.commandQueue = commandQueue
metalView.device = device
```

This code initializes the GPU and creates the command queue.

➤ After `super.init()`, add this:

```
metalView.clearColor = MTLClearColor(
  red: 1.0,
  green: 1.0,
  blue: 0.8,
  alpha: 1.0)
metalView.delegate = self
```

This code sets metalView.clearColor to a cream color. It also sets Renderer as the delegate for metalView so the view will call the MTKViewDelegate drawing methods.

➤ Build and run the app to make sure everything’s set up and working. If everything is good, you’ll see the SwiftUI view as before, and in the debug console, you’ll see the word “draw” repeatedly.

<a id="page-81"></a>

Note: You won’t see metalView’s cream color because you’re not asking the GPU to do any drawing yet.

## **Create the Mesh**

You’ve already created a sphere and a cone using Model I/O; now it’s time to create a cube.

➤ In `init(metalView:)`, before calling `super.init()`, add this:

```
// create the mesh
let allocator = MTKMeshBufferAllocator(device: device)
let size: Float = 0.8
let mdlMesh = MDLMesh(
  boxWithExtent: [size, size, size],
  segments: [1, 1, 1],
  inwardNormals: false,
  geometryType: .triangles,
  allocator: allocator)
do {
  mesh = try MTKMesh(mesh: mdlMesh, device: device)
} catch {
  print(error.localizedDescription)
}
```

This code creates the cube mesh, as you did in the previous chapter.

➤ Then, set up the `MTLBuffer` that contains the vertex data you’ll send to the GPU.

`vertexBuffer = mesh.vertexBuffers[0].buffer`

This code puts the mesh data in an MTLBuffer. Next, you need to set up the pipeline state so that the GPU will know how to render the data.

## **Set Up the Metal Library**

First, set up the MTLLibrary and ensure that the vertex and fragment shader functions are present.

➤ Continue adding code before super.init():

```
// create the shader function library
let library = device.makeDefaultLibrary()
Self.library = library
let vertexFunction = library?.makeFunction(name: "vertex_main")
```

<a id="page-82"></a>

```
let fragmentFunction =
  library?.makeFunction(name: "fragment_main")
```

Here, you set up the default library with some shader function pointers. You’ll create these shader functions later in this chapter. Shader functions are compiled when you compile your project and the compiled result is stored in the library.

## **Create the Pipeline State**

To configure the GPU’s state, you create a pipeline state object (PSO). This pipeline state can be a render pipeline state for rendering vertices, or a compute pipeline state for running a compute kernel.

➤ Continue adding code before super.init():

```
// create the pipeline state object
let pipelineDescriptor = MTLRenderPipelineDescriptor()
pipelineDescriptor.vertexFunction = vertexFunction
pipelineDescriptor.fragmentFunction = fragmentFunction
pipelineDescriptor.colorAttachments[0].pixelFormat =
  metalView.colorPixelFormat
pipelineDescriptor.vertexDescriptor =
  MTKMetalVertexDescriptorFromModelIO(mdlMesh.vertexDescriptor)
do {
  pipelineState =
    try device.makeRenderPipelineState(
      descriptor: pipelineDescriptor)
} catch {
  fatalError(error.localizedDescription)
}
```

The PSO holds a potential state for the GPU. The GPU needs to know its complete state before it can start managing vertices. Here, you set the two shader functions the GPU will call and the pixel format for the texture to which the GPU will write. You also set the pipeline’s vertex descriptor; this is how the GPU will know how to interpret the vertex data that you’ll present in the mesh data MTLBuffer.

Note: If you need to use a different data buffer layout or call different vertex or fragment functions, you’ll need additional pipeline states. Creating pipeline states is relatively time-consuming — which is why you do it up-front — but switching pipeline states during frames is fast and efficient.

The initialization is complete, and your project compiles. Next up, you’ll start on drawing your model.

<a id="page-83"></a>

## **Render Frames**

MTKView calls draw(in:) for every frame; this is where you’ll set up your GPU render commands.

➤ In `draw(in:)`, replace the `print` statement with this:

```
guard
  let commandBuffer = Self.commandQueue.makeCommandBuffer(),
  let descriptor = view.currentRenderPassDescriptor,
  let renderEncoder =
    commandBuffer.makeRenderCommandEncoder(
      descriptor: descriptor) else {
    return
}
```

You’ll send a series of commands to the GPU contained in command encoders. In one frame, you might have multiple command encoders, and the command buffer manages these.

![Figure](Metal_by_Tutorials_v500mpdf/0b42242a07de23c05867e63c.png)

_CPU commands_

You create a render command encoder using a render pass descriptor. This contains the render target textures that the GPU will draw into. In a complex app, you may well have multiple render passes in one frame, with multiple target textures. You’ll learn how to chain render passes together later.

<a id="page-84"></a>

➤ Continue adding this code:

```
// drawing code goes here

// 1
renderEncoder.endEncoding()
// 2
guard let drawable = view.currentDrawable else {
  return
}
commandBuffer.present(drawable)
// 3
commandBuffer.commit()
```

Here’s a closer look at the code:

1. After adding the GPU commands to a command encoder, you end its encoding.

2. You present the view’s drawable texture to the GPU.

3. When you commit the command buffer, you send the encoded commands to the GPU for execution.

## **Drawing**

It’s time to set up the list of commands that the GPU will need to draw your frame. In other words, you’ll:

• Set the pipeline state to configure the GPU hardware.

• Give the GPU the vertex data.

• Issue a draw call using the mesh’s submesh groups.

➤ Still in `draw(in:)`, replace the comment:

`// drawing code goes here`

With the following:

```
renderEncoder.setRenderPipelineState(pipelineState)
renderEncoder.setVertexBuffer(vertexBuffer, offset: 0, index: 0)
for submesh in mesh.submeshes {
  renderEncoder.drawIndexedPrimitives(
    type: .triangle,
    indexCount: submesh.indexCount,
    indexType: submesh.indexType,
    indexBuffer: submesh.indexBuffer.buffer,
```

<a id="page-85"></a>

```
    indexBufferOffset: submesh.indexBuffer.offset)
}
```

Great, you set up the GPU commands to set the pipeline state and the vertex buffer, and to perform the draw calls on the mesh’s submeshes. When you commit the command buffer at the end of draw(in:), you’re telling the GPU that the data and pipeline are ready, and it’s time for the GPU to take over.

## **The Render Pipeline**

Are you ready to investigate the GPU pipeline? Great, let’s get to it!

Apple Silicon’s Tile-Based Deferred Renderer (TBDR) GPU has two main rendering phases:

• The Tiling phase. Here’s where the GPU splits the screen into tiles and finds out which tile should process each vertex.

• The Rendering phase. The GPU will process all covered pixels during this phase.

By keeping these phases separate, the GPU can perform rendering at the same time as tiling, if GPU resources allow.

First, look at each of the processes in the tiling phase:

![Figure](Metal_by_Tutorials_v500mpdf/21f0e51b7a2cfab9b9ea067b.png)

_The Tiling phase_

<a id="page-86"></a>

## **Tiling: Vertex Fetch**

The name of this stage varies among different graphics Application Programming Interfaces (APIs). For example, DirectX calls it Input Assembler.

To start rendering 3D content, you first need a scene. A scene consists of models that have meshes of vertices.

![Figure](Metal_by_Tutorials_v500mpdf/a8dddc7e1e5d761e717787e1.png)

_Vertices in a scene_

As you saw in the previous chapter, you use a vertex descriptor to define the way vertices are read in along with their attributes — such as position, texture coordinates, normal and color.

When the GPU fetches the vertex buffer, the MTLRenderCommandEncoder draw call tells the GPU whether the buffer is indexed. If the buffer is not indexed, the GPU assumes the buffer is an array, and it reads in one element at a time, in order.

The GPU then sends the vertex data on to the **Vertex Processing** stage.

## **Tiling: Vertex Processing**

In the Vertex Processing stage, vertices are processed individually. This is your opportunity to write code to calculate per-vertex lighting and color. More importantly, you can transform vertex coordinates through various coordinate spaces to reach their position in the final render.

<a id="page-87"></a>

## **Creating a Vertex Shader**

It’s time to see vertex processing in action. The vertex shader you’re about to write is minimal, but it encapsulates most of the necessary vertex shader syntax you’ll need in this and subsequent chapters.

➤ Create a new file using the Metal File template, and name it Shaders.metal. Then, add this code at the end of the file:

```
// 1
struct VertexIn {
  float4 position [[attribute(0)]];
};

// 2
vertex float4 vertex_main(const VertexIn vertexIn [[stage_in]])
{
  return vertexIn.position;
}
```

Going through the code:

1. Create a VertexIn structure to describe the vertex attributes that match the vertex descriptor you set up earlier. In this case, just position.

2. Implement a vertex shader, vertex\_main, that takes in VertexIn structures and returns vertex positions as float4 types.

Remember in the current app, submeshes index the vertices in the vertex buffer. The vertex shader gets the current vertex index via the [[stage\_in]] attribute and unpacks the VertexIn structure cached for the vertex at the current index.

![Figure](Metal_by_Tutorials_v500mpdf/6bc0dfa5779c173493bc60b7.png)

_Vertex processing_

<a id="page-88"></a>

To recap, the CPU sent the GPU a vertex buffer that you created from the model’s mesh. You configured the vertex buffer using a vertex descriptor that tells the GPU how the vertex data is structured. On the GPU, you created a structure to encapsulate the vertex attributes. The vertex shader takes in this structure as a function argument, and through the [[stage\_in]] qualifier, acknowledges that position comes from the CPU via the [[attribute(0)]] position in the vertex buffer. The vertex shader then processes all of the vertices and returns their positions as a float4.

Note: When you use a vertex descriptor with attributes, you don’t have to match types. The MTLBuffer position is a float3, whereas VertexIn defines the position as a float4.

When the vertex shader has finished processing, the GPU then groups the vertices and passes them to the Primitive Assembly stage.

## **Tiling: Primitive Assembly**

The previous stage sent processed vertices grouped into blocks of data to this stage. The important thing to keep in mind is that vertices belonging to the same geometrical shape (primitive) are always in the same block. That means that the one vertex of a point, or the two vertices of a line, or the three vertices of a triangle, will always be in the same block, hence a second block fetch isn’t necessary.

![Figure](Metal_by_Tutorials_v500mpdf/54cd6ce1e17b7a057a2f8fe9.png)

_Primitive assembly_

<a id="page-89"></a>

Along with vertices, the CPU also sends vertex connectivity information when it issues the draw call command, like this:

```
renderEncoder.drawIndexedPrimitives(
  type: .triangle,
  indexCount: submesh.indexCount,
  indexType: submesh.indexType,
  indexBuffer: submesh.indexBuffer.buffer,
  indexBufferOffset: 0)
```

The first argument of the draw function contains the most important information about vertex connectivity. In this case, it tells the GPU that it should draw triangles from the vertex buffer it sent.

The Metal API provides five primitive types:

![Figure](Metal_by_Tutorials_v500mpdf/1f3db119dc69764c7ac7b2ac.png)

_The primitive types_

• point: For each vertex, rasterize a point. You can specify the size of a point that has the attribute [[point\_size]]\` in the vertex shader.

• line: For each pair of vertices, rasterize a line between them. If a vertex was already included in a line, it cannot be included again in other lines. The last vertex is ignored if there are an odd number of vertices.

<a id="page-90"></a>

• lineStrip: Same as a simple line, except that the line strip connects all adjacent vertices and forms a poly-line.Each vertex (except the first) is connected to the previous vertex.

• triangle: For every sequence of three vertices, rasterize a triangle. The last vertices are ignored if they cannot form another triangle.

• triangleStrip: Same as a simple triangle, except adjacent vertices can be connected to other triangles as well.

As you read in the previous chapter, the pipeline specifies the winding order of the vertices. If the winding order is counter-clockwise, and the triangle vertex order is counter-clockwise, the vertices are front-faced; otherwise, the vertices are back-faced and can be culled since you can’t see their color and lighting. Primitives are culled when they’re entirely occluded by other primitives.

However, if they’re only partially off-screen, they’ll be clipped.

![Figure](Metal_by_Tutorials_v500mpdf/d83fe2ccb57ccf6e5eda1ae1.png)

_Clipping primitives_

For efficiency, you should set winding order and enable back-face culling in the render command encoder before drawing.

<a id="page-91"></a>

## **Tiling: Tile Binning**

At this point, primitives that have made it through the culling and clipping process are binned into tiles and stored in on-chip tile memory, ready to move on to the rasterizer. This tile memory is an area of GPU memory not accessible by you. If it gets full during the draw call, it’s flushed and a partial render is done.

Each tile with its binned vertices now passes through the rendering phase:

![Figure](Metal_by_Tutorials_v500mpdf/265948fac732fad9ec747c8c.png)

_The rendering phase_

## **Rendering: Rasterization**

For each tile, taken from the Tiled Vertex Buffer, the rasterizer processes each primitive (usually triangles) in the scene, and works out which pixels should be rendered.

![Figure](Metal_by_Tutorials_v500mpdf/5f85f7bf89bdf321ab211b21.png)

_Rasterizing triangles_

<a id="page-92"></a>

## **Rendering: Hidden Surface Removal**

The rasterizer stores depth information, so that when a triangle fragment is in front of previous fragments, it keeps that fragment’s information and discards the others.

Traditional GPU architectures had to worry about overdraw, where pixels are rendered on top of one another.

In the following image, a blue cone is rendered in front of the train. In traditional GPUs, if the train is rendered before the cone, then both the yellow train pixels and the blue cone pixels would be calculated.

![Figure](Metal_by_Tutorials_v500mpdf/3f4c1e6b4a0bab03996d996a.png)

_Hidden surface removal_

With TBDR’s Hidden Surface Removal (HSR), the train’s pixels behind the cone won’t be calculated at all, no matter the order the objects are rendered in.

Note: Transparency and translucent objects are a little more complicated, but for now, you’ll just be rendering opaque objects.

<a id="page-93"></a>

## **Rendering: Fragment Processing**

When the rasterizer and HSR processes have worked out the visible fragments, fragment processing can begin. Here’s where you decide the color of each fragment.

Like vertex processing, the fragment processing stage is programmable. You create a fragment shader function that will receive the lighting, texture coordinate, depth and color information that the vertex function outputs. The fragment shader output is a single color for that fragment. Each of these fragments will contribute to the color of the final pixel in the framebuffer. All of the attributes are interpolated for each fragment.

![Figure](Metal_by_Tutorials_v500mpdf/3e6d5f385574d38d77db36ce.png)

_Fragment interpolation_

For example, to render this triangle, the vertex function would process three vertices with the colors red, green and blue. As the diagram shows, each fragment that makes up this triangle is interpolated from these three colors. Linear interpolation simply averages the color at each point on the line between two endpoints. If one endpoint has red color, and the other has green color, the midpoint on the line between them will be yellow. And so on.

The interpolation equation is parametric and has this form, where parameter p is the percentage (or a range from 0 to 1) of a color’s presence:

`newColor = p * oldColor1 + (1 - p) * oldColor2`

<a id="page-94"></a>

Color is easy to visualize, but the other vertex function outputs are also similarly interpolated for each fragment.

Note: If you don’t want a vertex output to be interpolated, add the attribute [[flat]] to its definition.

## **Creating a Fragment Shader**

➤ In **Shaders.Metal**, add the fragment function to the end of the file:

```
fragment float4 fragment_main() {
  return float4(1, 0, 0, 1);
}
```

This is the simplest fragment function possible. You return the interpolated color red in the form of a float4, which describes a color in RGBA format. All the fragments that make up the cube will be red.

## **Rendering: Framebuffer**

When fragments have been processed, Z (Depth) and Stencil Testing usually takes place. Fragments can be discarded if they fail the depth test, or are masked by a stencil buffer. An MTLDepthStencilState property on the render command encoder defines the rules for testing. You’ll create your first depth stencil state in Chapter 7, “The Fragment Function”.

Finally, the GPU blends the final colors and writes them to the render target, a special texture, also known as the framebuffer. The system then presents the framebuffer to the screen and refreshes the view’s pixel colors every frame. But it wouldn’t be very safe to write the color to the framebuffer while its being displayed on the screen.

A technique known as double-buffering is used to solve this situation. While the first buffer is being displayed on the screen, the second one is updated in the background. Then, the two buffers are swapped, and the second one is displayed on the screen while the first one is updated, and the cycle continues.

Whew! That was a lot of information to take in. However, the code you’ve written is what every Metal renderer uses, and despite just starting out, you should begin to recognize the rendering process when you look at Apple’s sample code.

<a id="page-95"></a>

➤ Build and run the app, and you’ll see a beautifully rendered red cube:

![Figure](Metal_by_Tutorials_v500mpdf/1a557acf7aaaff37216c5432.png)

_A rendered cube_

Notice how the cube is not square. Remember Metal uses Normalized Device Coordinates (NDC) that is -1 to 1 on the X axis. Resize your window, and the cube will maintain a size relative to the size of the window. In Chapter 6, “Coordinate Spaces”, you’ll learn how to position objects precisely on the screen.

What an incredible journey you’ve had through the rendering pipeline. In the next chapter, you’ll explore vertex and fragment shaders in greater detail.

<a id="page-96"></a>

## **Challenge**

Using the train.usdz model in the resources folder for this project, replace the cube with this train. When importing the model, be sure to copy files to destination, and remember to add the model to the target.

Change the model’s vertical position in the vertex function using this code:

```
float4 position = vertexIn.position;
position.y -= 1.0;
return position;
```

Finally, color your train blue.

![Figure](Metal_by_Tutorials_v500mpdf/04f621f8a259934597288ce6.png)

_Challenge result_

Refer to the previous chapter for asset loading and the vertex descriptor code if you need help. The finished code for this challenge is in the project challenge directory for this chapter.

<a id="page-97"></a>

## **Key Points**

• CPUs are best for processing sequential tasks fast, whereas GPUs excel at processing small tasks synchronously.

• SwiftUI is a great host for MTKViews, as you can layer UI elements easily.

• Separate Metal tasks where you can to the initialize phase. Initialize the device, command queues, pipeline states and model data buffers once at the start of your app.

• Each frame, create a command buffer and one or more command encoders.

• GPU architecture requires a strict pipeline. Configure this using PSOs (pipeline state objects).

• There are two programmable stages in a simple rendering GPU pipeline. You calculate vertex positions using the vertex shader, and calculate the color that appears on the screen using the fragment shader.

<a id="page-98"></a>

# 4

# Chapter 4: The Vertex Function

So far, you’ve worked your way through 3D models and the graphics pipeline. Now, it’s time to look at the first of two programmable stages in Metal, the vertex stage — and more specifically, the vertex function.

## **Shader Functions**

When you define a shader function, you assign it an attribute. The attributes you’ll learn about in this book are:

• vertex: Vertex function: Calculates the position of a vertex.

• fragment: Fragment function: Calculates the color of a fragment.

• kernel: Kernel function: Used for general-purpose parallel computations, such as image processing.

• mesh: Mesh function: Replaces the vertex shader pipeline, and outputs constructed geometry directly to the rasterizer.

• object: Object function: Part of the mesh shader pipeline, the object function determines which objects the mesh function will process.

<a id="page-99"></a>

In this chapter, you’ll focus only on the vertex function, and see how you can calculate the position, along with other attributes, of each vertex.

By now, you should be familiar with vertex descriptors, and how to use them to describe how to lay out the vertex attributes from your loaded 3D model. To recap:

• MDLVertexDescriptor: The Model I/O vertex descriptor determines the format when you read in a USD file. Model I/O creates buffers with the desired layout of attributes, such as position, normals and texture coordinates.

• MTLVertexDescriptor: You use a Metal vertex descriptor when creating the pipeline state. The GPU vertex function uses the [[stage\_in]] attribute to match the incoming data with the vertex descriptor in the pipeline state.

As you work through this chapter, you’ll construct your own vertex mesh and send vertices to the GPU without using a vertex descriptor. You’ll learn how to manipulate these vertices in the vertex function, and then you’ll upgrade to using a vertex descriptor. In the process, you’ll see how using Model I/O to import your meshes does a lot of the heavy lifting for you.

## **The Starter Project**

➤ Open the starter project for this chapter.

This SwiftUI project contains a reduced Renderer so that you can add your own mesh, and the shader functions are bare-bones so that you can build them up. You’re not doing any drawing yet, so there’s nothing to see when you run the app.

<a id="page-100"></a>

## **Rendering a Quad**

You create a quad using two triangles. Each triangle has three vertices, for a total of six vertices.

![Figure](Metal_by_Tutorials_v500mpdf/98c1ccd34d4acf032aebed8c.png)

_A quad mesh_

➤ Create a new Swift file named Quad.swift.

➤ Replace the existing code with:

```
import MetalKit

struct Vertex {
  var x: Float
  var y: Float
  var z: Float
}

struct Quad {
  var vertices: [Vertex] = [
    Vertex(x: -1, y:  1, z: 0),    // triangle 1
    Vertex(x:  1, y: -1, z: 0),
    Vertex(x: -1, y: -1, z: 0),
    Vertex(x: -1, y:  1, z: 0),    // triangle 2
    Vertex(x:  1, y:  1, z: 0),
    Vertex(x:  1, y: -1, z: 0)
  ]
}
```

<a id="page-101"></a>

You create a structure to make up a vertex with an x, y and z value. Here, the winding order (the vertex order) of the vertices is clockwise, which is important.

➤ Add a new vertex buffer property to `Quad` and initialize it:

```
let vertexBuffer: MTLBuffer

init(device: MTLDevice, scale: Float = 1) {
  vertices = vertices.map {
    Vertex(x: $0.x * scale, y: $0.y * scale, z: $0.z * scale)
  }
  guard let vertexBuffer = device.makeBuffer(
    bytes: &vertices,
    length: MemoryLayout<Vertex>.stride * vertices.count,
    options: []) else {
    fatalError("Unable to create quad vertex buffer")
  }
  self.vertexBuffer = vertexBuffer
}
```

With this code, you initialize the Metal buffer with the array of vertices. You multiply each vertex by scale, which lets you set the size of the quad during initialization.

➤ Open **Renderer.swift**, and add a new property for the quad mesh:

```
lazy var quad: Quad = {
  Quad(device: Self.device, scale: 0.8)
}()
```

Here, you initialize quad with Renderer’s device. You must initialize quad lazily because device is not initialized until init(metalView:) is run. You also resize the quad so that you can see it properly.

Note: If you were to leave the scale at the default of 1.0, the quad would cover the entire screen. Covering the screen is useful for full-screen drawing since the fragment function will only draw where there is geometry covering that fragment.

➤ In `draw(in:)`, after `// do drawing here`, add:

```
renderEncoder.setVertexBuffer(
  quad.vertexBuffer,
  offset: 0,
  index: 0)
```

<a id="page-102"></a>

You create a command on the render command encoder to set the vertex buffer in the buffer argument table at index 0.

➤ Add the draw call:

```
renderEncoder.drawPrimitives(
  type: .triangle,
  vertexStart: 0,
  vertexCount: quad.vertices.count)
```

Here, you draw the quad’s six vertices.

➤ Open Shaders.metal.

➤ Replace the vertex function with:

```
vertex float4 vertex_main(
  constant float3 *vertices [[buffer(0)]],
  uint vertexID [[vertex_id]])
{
  float4 position = float4(vertices[vertexID], 1);
  return position;
}
```

There’s an error with this code, which you’ll observe and fix shortly.

The GPU performs the vertex function for each vertex. In the draw call, you specified that there are six vertices. So, the vertex function will perform six times in parallel (all at the same time in different threads).

When you pass a pointer into the vertex function, you must specify an address space, either constant or device. constant is optimized for accessing the same variable over several vertex functions in parallel. device is best for accessing different parts of a buffer over the parallel functions — such as when using a buffer with points and color data interleaved.

[[vertex\_id]] is an attribute qualifier that gives you the current vertex. You can use this as an entry into the array held in vertices.

You might notice that you’re sending the GPU a buffer that you filled with an array of Vertexs, consisting of three Floats. In the vertex function, you read the same buffer as an array of float3s, leading to an error in the display.

<a id="page-103"></a>

➤ Build and run.

![Figure](Metal_by_Tutorials_v500mpdf/757e4c58edeb80af972e0500.png)

_A rendering error_

Although you might get a different render, the vertices are in the wrong position because a float3 type takes up more memory than Vertex with its three Float types. A Float is 4 bytes long, and Vertex is 12 bytes long. The SIMD float3 type is padded and takes up the same memory as the float4 type, which is 16 bytes. Changing this parameter to a packed\_float3 will fix the error since a packed\_float3 takes up 12 bytes.

Note: You can check the sizes of types in the Metal Shading Language Specification at https://apple.co/2UT993x.

➤ In the vertex function, change float3 in the first parameter to packed\_float3.

➤ Build and run.

![Figure](Metal_by_Tutorials_v500mpdf/86bc4a9de9e4e1e801e2501f.png)

_The rendering error corrected_

The quad now displays correctly.  Alternatively, you could have defined the Float array vertices as an array of simd\_float3. In that case, you’d use float3 in the vertex function, as both types take 16 bytes. However, sending 16 bytes per vertex is slightly less efficient than sending 12 bytes per vertex.

<a id="page-104"></a>

## **Calculating Positions**

Metal is all about gorgeous graphics and fast, smooth animation. As a next step, you’ll make your quad move up and down the screen. To do this, you’ll have a timer that updates every frame, and the position of each vertex will depend on this timer.

The vertex function is where you update vertex positions, so you’ll send the timer data to the GPU.

➤ Open Renderer.swift, and add a new property to Renderer:

`var timer: Float = 0`

➤ In `draw(in:)`, right before:

`renderEncoder.setRenderPipelineState(pipelineState)`

➤ Add the following code:

```
// 1
timer += 0.005
var currentTime = sin(timer)
// 2
renderEncoder.setVertexBytes(
  &currentTime,
  length: MemoryLayout<Float>.stride,
  index: 11)
```

Let’s have a closer look:

1. For every frame, you update the timer. You want your cube to move up and down the screen, so you’ll use a value between -1 and 1. Using sin() is a great way to achieve this balance as sine values are always -1 to 1. You can change the speed of your animation by changing the value that you add to this timer for each frame.

2. If you’re only sending a small amount of data, less than 4KB, to the GPU, setVertexBytes(\_:length:index:) is an alternative to setting up an MTLBuffer. Here, you set currentTime to index 11 in the buffer argument table. Keeping buffers 1 through 10 for vertex attributes — such as vertex positions — helps you to remember which buffers hold what data.

<a id="page-105"></a>

➤ Open **Shaders.metal**, and replace the vertex function with this code:

```
vertex float4 vertex_main(
  constant packed_float3 *vertices [[buffer(0)]],
  constant float &timer [[buffer(11)]],
  uint vertexID [[vertex_id]])
{
  float4 position = float4(vertices[vertexID], 1);
  position.y += timer;
  return position;
}
```

You receive the single value timer as a float in buffer 11. You add the timer value to the y position and return the new position from the function.

In the next chapter, you’ll start learning how to project vertices into 3D space using matrix multiplication. But you don’t always need matrix multiplication to move vertices; here, you can achieve the translation of the position in y using simple addition.

➤ Build and run the app, and you’ll see a lovely animated quad.

![Figure](Metal_by_Tutorials_v500mpdf/c0e3c9325d6058da30532bdb.png)

_An animated quad_

<a id="page-106"></a>

## More Efﬁcient Rendering

Currently, you’re using six vertices to render two triangles.

![Figure](Metal_by_Tutorials_v500mpdf/939122ac1f100f4a16098736.png)

_The mesh of two triangles_

Of those vertices, 0 and 3 are in the same position, as are 1 and 5. If you render a mesh with thousands — or even millions of vertices, it’s important to reduce duplication as much as possible. You can do this with indexed rendering.

Create a structure of only unique positions, and then use indices to get the right position for a vertex.

➤ Open Quad.swift, and rename vertices to oldVertices.

➤ Add the following structures to Quad:

```
var vertices: [Vertex] = [
  Vertex(x: -1, y:  1, z: 0),
  Vertex(x:  1, y:  1, z: 0),
  Vertex(x: -1, y: -1, z: 0),
  Vertex(x:  1, y: -1, z: 0)
]

var indices: [UInt16] = [
  0, 3, 2,
  0, 1, 3
]
```

vertices now holds the unique four points of the quad in any order. indices holds the index of each vertex in the correct vertex order. Refer to oldVertices to make sure your indices are correct.

<a id="page-107"></a>

➤ Add a new Metal buffer to hold indices:

`let indexBuffer: MTLBuffer`

➤ At the end of `init(device:scale:)`, add:

```
guard let indexBuffer = device.makeBuffer(
  bytes: &indices,
  length: MemoryLayout<UInt16>.stride * indices.count,
  options: []) else {
  fatalError("Unable to create quad index buffer")
}
self.indexBuffer = indexBuffer
```

You create the index buffer the same way you did the vertex buffer.

➤ Open **Renderer.swift**, and in `draw(in:)` before the draw call, add:

```
renderEncoder.setVertexBuffer(
  quad.indexBuffer,
  offset: 0,
  index: 1)
```

Here, you send the index buffer to the GPU.

➤ Change the draw call to:

```
renderEncoder.drawPrimitives(
  type: .triangle,
  vertexStart: 0,
  vertexCount: quad.indices.count)
```

Use the index count for the number of vertices to render; not the vertex count.

➤ Open **Shaders.metal**, and change the vertex function to:

```
vertex float4 vertex_main(
  constant packed_float3 *vertices [[buffer(0)]],
  constant ushort *indices [[buffer(1)]],
  constant float &timer [[buffer(11)]],
  uint vertexID [[vertex_id]])
{
  ushort index = indices[vertexID];
  float4 position = float4(vertices[index], 1);
  return position;
}
```

Here, vertexID is the index into the buffer holding the quad indices. You use the value in the indices buffer to index the correct vertex in the vertex buffer.

<a id="page-108"></a>

➤ Build and run. Sure, your quad is positioned the same way as before, but now you’re sending less data to the GPU.

![Figure](Metal_by_Tutorials_v500mpdf/4a44e55fdd99b04a42e5751e.png)

_Indexed mesh_

From the number of entries in arrays, it might appear as if you’re actually sending more data — but you’re not! The memory footprint of oldVertices is 72 bytes, whereas the footprint of vertices + indices is 60 bytes.

## **Vertex Descriptors**

A more efficient draw call is available when you use indices for rendering vertices. However, you first need to set up a vertex descriptor in the pipeline.

It’s usually a good idea to use vertex descriptors, as most often, you won’t only send positions to the GPU. You’ll also send attributes such as normals, texture coordinates and colors. When you can lay out your own vertex data, you have more control over how your engine handles model meshes.

➤ Create a new Swift file named **VertexDescriptor.swift** and replace the code with:

```
import MetalKit

extension MTLVertexDescriptor {
  static var defaultLayout: MTLVertexDescriptor {
    let vertexDescriptor = MTLVertexDescriptor()
    vertexDescriptor.attributes[0].format = .float3
    vertexDescriptor.attributes[0].offset = 0
    vertexDescriptor.attributes[0].bufferIndex = 0

    let stride = MemoryLayout<Vertex>.stride
    vertexDescriptor.layouts[0].stride = stride
    return vertexDescriptor
```

<a id="page-109"></a>

```
  }
}
```

Here, you set up a vertex layout that has only one attribute. This attribute describes the position of each vertex.

A vertex descriptor holds arrays of attributes and buffer layouts.

• attributes: For each attribute, you specify the type format and offset in bytes of the first item from the beginning of the buffer. You also specify the index into the buffer argument table of this attribute’s buffer.

• buffer layout: You specify the length of the stride of all attributes combined in each buffer. It may be confusing here as you’re using index 0 to index into both layouts and attributes, but the layouts index 0 corresponds to the bufferIndex 0 used by attributes.

Note: stride describes how many bytes are between each instance. Due to internal padding and byte alignment, this value can be different from size. For an excellent explanation of size, stride and alignment, check out Greg Heo’s article at https://bit.ly/2V3gBJl.

To the GPU, the `vertexBuffer` now looks like this:

![Figure](Metal_by_Tutorials_v500mpdf/cff270539101bcb2f5f11483.png)

_Vertex buffer layout_

➤ Open Renderer.swift, and locate where you create the pipeline state in init(metalView:).

<a id="page-110"></a>

➤ Before creating the pipeline state in do {}, add the following code to the pipeline state descriptor:

```
pipelineDescriptor.vertexDescriptor =
  MTLVertexDescriptor.defaultLayout
```

The GPU will now expect vertices in the format described by this vertex descriptor.

➤ In `draw(in:)`, remove:

```
renderEncoder.setVertexBuffer(
  quad.indexBuffer,
  offset: 0,
  index: 1)
```

You’ll include the index buffer in the draw call.

➤ Change the draw call to:

```
renderEncoder.drawIndexedPrimitives(
  type: .triangle,
  indexCount: quad.indices.count,
  indexType: .uint16,
  indexBuffer: quad.indexBuffer,
  indexBufferOffset: 0)
```

This draw call expects the index buffer to use UInt16, which is how you described your indices array in Quad. You don’t explicitly send quad.indexBuffer to the GPU because this draw call will do it for you.

➤ Open **Shaders.metal** and replace the vertex function with:

```
vertex float4 vertex_main(
  float4 position [[attribute(0)]] [[stage_in]],
  constant float &timer [[buffer(11)]])
{
  return position;
}
```

You did all the heavy lifting for the layout on the Swift side, so that takes the size of the vertex function way down.

<a id="page-111"></a>

You describe each per-vertex input with the [[stage\_in]] attribute. The GPU now looks at the pipeline state’s vertex descriptor.

[[attribute(0)]] is the attribute in the vertex descriptor that describes the position. Even though you defined your original vertex data as type Vertex containing three Floats, you can define the position as float4 here. The GPU can make the conversion.

It’s worth noting that when the GPU adds the w information to the xyz position, it adds 1.0. As you’ll see in the following chapters, this w value is important during rasterization.

The GPU now has all of the information it needs to calculate the position for each vertex.

➤ Build and run the app to ensure that everything still works. The resulting render will be the same as before.

![Figure](Metal_by_Tutorials_v500mpdf/81f97372c0503aebb789a200.png)

_Rendering using a vertex descriptor_

## **Adding Another Vertex Attribute**

You probably won’t ever have just one attribute, so let’s add a color attribute for each vertex.

You have a choice whether to use two buffers or interleave the color between each vertex position. If you choose to interleave, you’ll set up a structure to hold position and color. In this example, however, it’s easier to add a new colors buffer to match each vertex.

<a id="page-112"></a>

➤ Open **Quad.swift**, and add the new array:

```
var colors: [simd_float3] = [
  [1, 0, 0], // red
  [0, 1, 0], // green
  [0, 0, 1], // blue
  [1, 1, 0]  // yellow
]
```

You now have four RGB colors to match the four vertices.

➤ Create a new buffer property:

`let colorBuffer: MTLBuffer`

➤ At the end of `init(device:scale:)`, add:

```
guard let colorBuffer = device.makeBuffer(
  bytes: &colors,
  length: MemoryLayout<simd_float3>.stride * colors.count,
  options: []) else {
    fatalError("Unable to create quad color buffer")
  }
self.colorBuffer = colorBuffer
```

You initialize `colorBuffer` the same way as the previous two buffers.

➤ Open **Renderer.swift**, and in `draw(in:)` right before the draw call, add:

```
renderEncoder.setVertexBuffer(
  quad.colorBuffer,
  offset: 0,
  index: 1)
```

You send the color buffer to the GPU using argument table buffer index 1, which must match the index in the vertex descriptor layout.

➤ Open VertexDescriptor.swift, and add the following code to defaultLayout before return:

```
vertexDescriptor.attributes[1].format = .float3
vertexDescriptor.attributes[1].offset = 0
vertexDescriptor.attributes[1].bufferIndex = 1
vertexDescriptor.layouts[1].stride =
  MemoryLayout<simd_float3>.stride
```

Here, you describe the layout of the color buffer in buffer index 1.

<a id="page-113"></a>

➤ Open Shaders.metal.

➤ You can only use [[stage\_in]] on one parameter, so create a new structure before the vertex function:

```
struct VertexIn {
  float4 position [[attribute(0)]];
  float4 color [[attribute(1)]];
};
```

➤ Change the vertex function to:

```
vertex float4 vertex_main(
  VertexIn in [[stage_in]],
  constant float &timer [[buffer(11)]])
{
  return in.position;
}
```

This code is still short and concise. The GPU knows how to retrieve position and color from the buffers because of the [[attribute(n)]] qualifier in the structure, which looks at the pipeline state’s vertex descriptor.

➤ Build and run to ensure your blue quad still renders.

![Figure](Metal_by_Tutorials_v500mpdf/4a6f14d028fd88d7471685b4.png)

_Quad with two attributes_

The fragment function determines the color of each rendered fragment. You need to pass the vertex’s color to the fragment function. You’ll learn more about the fragment function in Chapter 7, “The Fragment Function”.

➤ Still in **Shaders.metal**, add this structure before the vertex function:

```
struct VertexOut {
  float4 position [[position]];
```

<a id="page-114"></a>

```
  float4 color;
};
```

Instead of returning just the position from the vertex function, you’ll now return both position and color. You specify a position attribute to let the GPU know which property in this structure is the position.

➤ Replace the vertex function with:

```
vertex VertexOut vertex_main(
  VertexIn in [[stage_in]],
  constant float &timer [[buffer(11)]]) {
  VertexOut out {
   .position = in.position,
   .color = in.color
  };
  return out;
}
```

You now return a VertexOut instead of a float4.

➤ Change the fragment function to:

```
fragment float4 fragment_main(VertexOut in [[stage_in]]) {
  return in.color;
}
```

The [[stage\_in]] attribute indicates that the GPU should take the VertexOut output from the vertex function and match it with the rasterized fragments. Here, you return the vertex color. Remember from Chapter 3, “The Rendering Pipeline”, that each fragment’s input gets interpolated.

➤ Build and run the app, and you’ll see the quad rendered with beautiful colors.

![Figure](Metal_by_Tutorials_v500mpdf/942a65c94a67a8c36d4edfb0.png)

_Interpolated vertex colors_

<a id="page-115"></a>

## **Rendering Points**

Instead of rendering triangles, you can render points and lines.

➤ Open **Renderer.swift**, and in `draw(in:)`, change:

```
renderEncoder.drawIndexedPrimitives(
  type: .triangle,
```

➤ To:

```
renderEncoder.drawIndexedPrimitives(
  type: .point,
```

If you build and run now, the GPU will render the points, but it doesn’t know what point size to use, so it flickers over various point sizes. To fix this problem, you’ll also return a point size when returning data from the vertex function.

➤ Open Shaders.metal, and add this property to VertexOut:

`float pointSize [[point_size]];`

The `[[point_size]]` attribute will tell the GPU what point size to use.

➤ In `vertex_main`, replace the initialization of `out` with:

```
VertexOut out {
  .position = in.position,
  .color = in.color,
  .pointSize = 30
};
```

Here, you assign the point size of 30.

➤ Build and run to see your points rendered with their vertex color:

![Figure](Metal_by_Tutorials_v500mpdf/5338fd8b2e079e8d74190a18.png)

_Rendering points_

<a id="page-116"></a>

## **Challenge**

So far, you’ve sent vertex positions to the GPU in an array buffer. But this isn’t entirely necessary. All the GPU needs to know is how many vertices to draw. Your challenge is to remove the vertex and index buffers, and draw 50 points in a circle. Here’s an overview of the steps you’ll need to take, along with some code to get you started:

1. In Renderer, remove the vertex descriptor from the pipeline.

2. Replace the draw call in Renderer so that it doesn’t use indices but does draw 50 vertices.

3. In draw(in:), remove all of the setVertexBuffer commands.

4. The GPU will need to know the total number of points, so send this value the same way you did timer. Use buffer 0 for the number of points.

5. Replace the vertex function with:

```
vertex VertexOut vertex_main(
  constant uint &count [[buffer(0)]],
  constant float &timer [[buffer(11)]],
  uint vertexID [[vertex_id]])
{
  float radius = 0.8;
  float current = float(vertexID) / float(count);
  float2 position;
  position.x = radius * cos(2 * M_PI_F * current);
  position.y = radius * sin(2 * M_PI_F * current);
  VertexOut out {
      .position = float4(position, 0, 1),
      .color = float4(1, 0, 0, 1),
      .pointSize = 20
  };
  return out;
}
```

<a id="page-117"></a>

Remember, this is an exercise to help you understand how to position points on the GPU without holding any equivalent data on the Swift side. So, don’t worry too much about the math. In this function, you use the sine and cosine of the current vertex ID to plot the point around a circle.

Build and run to see your 50 points plotted into a circle.

![Figure](Metal_by_Tutorials_v500mpdf/a7fe304b25dddcf9b9f1efbd.png)

_Points in a circle_

Try animating the points by adding timer to current.

If you have any difficulties, you can find the solution in the project challenge directory for this chapter.

<a id="page-118"></a>

## **Key Points**

• The vertex function’s fundamental task is positioning vertices. When you render a model, you send the GPU the model’s vertices in its original zero position. The vertex shader will then calculate the new position of those vertices to the correct spot in your 3D world.

• Shader code uses attributes such as [[buffer(0)]] and [[position]] extensively. To find out more about these attributes, refer to the Metal Shading Language specification document (https://apple.co/3hPTbjQ).

• You can pass any data in an MTLBuffer to the GPU using setVertexBuffer(\_:offset:index:). If the data is less than 4KB, you don’t have to set up a buffer; you can, instead, pass a structure using setVertexBytes(\_:length:index:).

• When possible, use indexed rendering. With indexed rendering, you pass less data to the GPU — and memory bandwidth is a major bottleneck.

• When possible, use vertex descriptors. With the vertex descriptor held in the pipeline state object, the GPU knows the format of the data being passed, and you’ll get fewer errors in your code when you change a type on the Swift side and forget to change the shader function.

<a id="page-119"></a>

# 5

# Chapter 5: 3D Transformations

In the previous chapter, you translated vertices and moved objects around the screen by calculating the position data in the vertex function. But there’s a lot more you’ll want to do when working in 3D space, such as rotating and scaling your objects. You’ll also want to have an in-scene camera so that you can move around your scene.

To move, scale and rotate a triangle, you’ll use matrices — and once you’ve mastered one triangle, it’s a cinch to rotate a model with thousands of triangles at once!

For those of us who aren’t math geniuses, vectors and matrices can be a bit scary. Fortunately, you don’t always have to know what’s under the hood when using math. To help, this chapter focuses not on the math, but the matrices. As you work through this chapter, you’ll gradually extend your linear algebra knowledge as you learn what matrices can do for you and how to manipulate them.

<a id="page-120"></a>

## **Transformations**

Look at the following picture:

![Figure](Metal_by_Tutorials_v500mpdf/413f2b4138e36c88518d5fc7.png)

_Affine Transformations_

Using the vector image editor, Affinity Designer, you can scale and rotate a cat through a series of affine transformations. Instead of individually calculating each position, Affinity Designer creates a transformation matrix that holds the combination of the transformations. It then applies the transformation to each element.

Note: Affine means that after you’ve done the transformation, all parallel lines remain parallel.

Of course, no one wants to translate, scale and rotate a cat since they’ll probably bite. So instead, you’ll translate, scale and rotate a triangle.

<a id="page-121"></a>

## **The Starter Project & Setup**

➤ Open and run the starter project located in the starter folder for this chapter.

![Figure](Metal_by_Tutorials_v500mpdf/fc06f43639f34dc102a7afaf.png)

_The starter project_

This project renders a Triangle twice rather than a Quad.

In Renderer, in draw(in:), you’ll see two draw calls (one for each triangle). Renderer passes position to the vertex function and color to the fragment function; it does this for each triangle. The gray triangle is at its original position, and the red triangle has transformations.

➤ Before moving on to the next step, make sure you understand the code in Renderer’s draw(in:) and the vertex function in Shaders.metal.

ContentView.swift is now located in the SwiftUI Views folder, and it displays a grid over the metal view so that you can visualize your vertex positions more easily.

<a id="page-122"></a>

## **Translation**

The starter project renders two triangles:

• A gray triangle without any transformations.

• A red triangle translated with var newPosition = simd\_float3(0.3, -0.4, 0).

![Figure](Metal_by_Tutorials_v500mpdf/fe1afa1584f13a80d8375712.png)

_Displacement Vectors_

In the first challenge in the previous chapter, you calculated the position of each vertex in the shader function. A more common computer graphics paradigm is to create a vertex position buffer at the start of the app, usually loaded from a file, containing the original position of each vertex of the model. Then, on each frame, send an offset matrix to the vertex shader that contains the model’s current position, rotation and scale. You can then multiply each original position in the buffer by this offset matrix on the GPU to transform to the new position.

## **Vectors & Matrices**

You can better describe position as a displacement vector of [0.3, -0.4, 0]. You move each vertex 0.3 units in the x-direction, and -0.4 in the y-direction from its starting position.

<a id="page-123"></a>

In the following image, the blue arrows are vectors.

![Figure](Metal_by_Tutorials_v500mpdf/bd9da19a8fd0468995d2921f.png)

_Vectors_

The left blue arrow is a vector with a value of [-1, 2]. The right blue arrow — the one near the cat — is also a vector with a value of [-1, 2]. Positions (points) are locations in space, whereas vectors are displacements in space. In other words, a vector contains the amount and direction to move. If you were to displace the cat by the blue vector, it would end up at point (2, 4). That’s the cat’s position (3, 2) plus the vector [-1, 2].

This 2D vector is a **1x2** matrix. It has one column and two rows.

Note: You can order Matrices by rows or columns. The simd library constructs matrices in column-major order, which means that columns are contiguous in memory. A simd\_double2x4 is a matrix of two columns and four rows.

<a id="page-124"></a>

A matrix is a two-dimensional array. Even the single number 1 is a 1×1 matrix. In fact, the number 1 is unique in that when you multiply a number by 1, the answer is always that number. All square matrices — where the array width is the same as the array height — have a matrix with this same property. It’s called the identity matrix. Any vector or matrix multiplied by an identity matrix returns the same value.

A 4×4 identity matrix looks like this (all zeros, except for the diagonal 1s):

![Figure](Metal_by_Tutorials_v500mpdf/992cc4a2a773e275a4895e85.png)

_An identity matrix_

A 3D transformation matrix has four rows and four columns. A transformation matrix holds scaling and rotation information in the upper left 3×3 matrix, with the translation information in the last column. When you multiply vectors and matrices, the number of columns of the left side matrix or vector must equal the number of rows of the right side. For example, you can’t multiply a float3 by a float4×4.

## **The Magic of Matrices**

When you multiply matrices, you combine them into one matrix. You can then multiply a vector by this matrix to transform the vector. For example, you can set up a rotation matrix and a translation matrix. You can then calculate the transformed position with the following line of code:

`translationMatrix * rotationMatrix * positionVector`

Matrix multiplication goes from right to left. Here, the rotation is applied to the position before the translation.

This is a fundamental of linear algebra — and if you want to continue with computer graphics, you’ll need to understand linear algebra more fully. For now, understanding the concepts of setting up a transformation matrix can take you a long way.

<a id="page-125"></a>

## **Creating a Matrix**

➤ Open Renderer.swift, and locate where you render the first gray triangle in draw(in:).

➤ Change the position code from:

```
var originalPosition = simd_float3(0, 0, 0)
renderEncoder.setVertexBytes(
  &originalPosition,
  length: MemoryLayout<SIMD3<Float>>.stride,
  index: 11)
```

➤ To:

```
var translation = matrix_float4x4()
translation.columns.0 = [1, 0, 0, 0]
translation.columns.1 = [0, 1, 0, 0]
translation.columns.2 = [0, 0, 1, 0]
translation.columns.3 = [0, 0, 0, 1]
var matrix = translation
renderEncoder.setVertexBytes(
  &matrix,
  length: MemoryLayout<matrix_float4x4>.stride,
  index: 11)
```

Here, you create an identity matrix and a render command to send to the GPU.

➤ Locate the position code for the second red triangle and change:

```
var newPosition = simd_float3(0.3, -0.4, 0)
renderEncoder.setVertexBytes(
  &newPosition,
  length: MemoryLayout<SIMD3<Float>>.stride,
  index: 11)
```

➤ To:

```
let newPosition = simd_float3(0.3, -0.4, 0)
translation.columns.3.x = newPosition.x
translation.columns.3.y = newPosition.y
translation.columns.3.z = newPosition.z
matrix = translation
renderEncoder.setVertexBytes(
  &matrix,
  length: MemoryLayout<matrix_float4x4>.stride,
  index: 11)
```

<a id="page-126"></a>

You’ll use this matrix to translate the position in the vertex shader.

➤ Open **Shaders.metal** and change:

`constant float3 &position [[buffer(11)]])`

➤ To:

`constant float4x4 &matrix [[buffer(11)]])`

You receive the matrix into the shader.

➤ In the vertex function, change:

`float3 translation = in.position.xyz + position;`

➤ To:

`float3 translation = in.position.xyz + matrix.columns[3].xyz;`

You use the fourth column of the matrix as the displacement vector.

➤ Build and run. So far, the output is the same.

![Figure](Metal_by_Tutorials_v500mpdf/f4456a2731d95358105850e2.png)

_Translation by adding a matrix column to the position_

<a id="page-127"></a>

Remember this matrix is also going to hold rotation and scaling information. To calculate the position, instead of adding the translation displacement vector, you’ll do matrix multiplication.

➤ Change the contents of the vertex function to:

```
float4 translation = matrix * in.position;
VertexOut out {
  .position = translation
};
return out;
```

➤ Build and run the app, and you’ll see there’s still no change.

You can now add scaling and rotation to the matrix in Renderer without having to change the shader function each time.

## **Scaling**

➤ Open Renderer.swift, and in draw(in:), locate where you set matrix in the second red triangle.

➤ Before `matrix = translation`, add this:

```
let scaleX: Float = 1.2
let scaleY: Float = 0.5
let scaleMatrix = float4x4(
  [scaleX, 0,   0,   0],
  [0, scaleY,   0,   0],
  [0,      0,   1,   0],
  [0,      0,   0,   1])
```

Instead of assigning to columns as you did for the translation, you can initialize a matrix like this, defining the columns as arrays. scaleMatrix.columns.0 now contains [1.2, 0, 0, 0]

Without going into mathematics too much, you can use this code to set up a scale matrix.

➤ Change `matrix = translation` to:

`matrix = scaleMatrix`

You multiply the translation matrix by the scale matrix instead of the translation matrix.

<a id="page-128"></a>

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/107ac81d58cf6fa9cae4fe16.png)

_Scaling with a matrix_

In the vertex function, the matrix multiplies each vertex of the triangle by the x and y scales.

➤ Change `matrix = scaleMatrix` to:

`matrix = translation * scaleMatrix`

This code translates the scaled triangle.

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/10fab5f711363393502e33fd.png)

_A translated and scaled triangle_

<a id="page-129"></a>

## **Rotation**

You perform rotation in a similar way to scaling.

➤ Change `matrix = translation * scaleMatrix`, to this:

```
let angle = Float.pi / 2.0
let rotationMatrix = float4x4(
  [cos(angle), -sin(angle), 0,    0],
  [sin(angle),  cos(angle), 0,    0],
  [0,           0,          1,    0],
  [0,           0,          0,    1])

matrix = rotationMatrix
```

Here, you set a rotation around the z-axis of the angle in radians.

Note: Float.pi / 2.0 is the same as 90º, which is 1.5708 radians. A radian is the standard unit in computer graphics. This is the formula to convert degrees to radians: degrees \* pi / 180 = radians.

➤ Build and run, and you’ll see how each of the vertices of the red triangle are rotated by 90º around the origin [0, 0, 0].

![Figure](Metal_by_Tutorials_v500mpdf/b1e82fa21a01fc2a114a74e4.png)

_Rotating about the origin_

<a id="page-130"></a>

➤ Replace `matrix = rotationMatrix` with:

`matrix = translation * rotationMatrix * scaleMatrix`

This code first scales each vertex, then rotates, then translates.

➤ Build and run.

![Figure](Metal_by_Tutorials_v500mpdf/83fb4bf1027c9f511bb02ee2.png)

_Scale, rotate and translate_

The order of matrix operations is important. Experiment with changing the order to see what happens.

Scaling and rotation take place at the origin point (coordinates [0, 0, 0]). There may be times, however, that you want the rotation to take place around a different point. For example, let’s rotate the triangle around the right-most point of the triangle when it’s in its identity position (i.e., the same position and rotation as the gray triangle).

To rotate the triangle, you’ll set up a translation matrix with the vector between the origin and the right-most point, taking the following steps:

1. Translate all the vertices using the translation matrix.

2. Rotate.

3. Translate back again.

<a id="page-131"></a>

➤ Before setting `matrix` in the red triangle, add this code:

```
translation.columns.3.x = triangle.vertices[2].x
translation.columns.3.y = triangle.vertices[2].y
translation.columns.3.z = triangle.vertices[2].z
```

You set the translation matrix to move to the third vertex of the triangle, which is the right-most point.

Remember the steps. Step 1 is to translate all of the vertices by the distance from the origin. You can achieve this by setting a matrix to the vertex’s vector value and using the translate matrix’s inverse.

Don’t forget to build and run the app after each of the following steps so that you can see what the matrix multiplication is doing.

➤ Change `matrix = translation * rotationMatrix * scaleMatrix` to:

`matrix = translation.inverse`

This code places the right-most vertex at the origin, translating all other vertices by the same amount.

![Figure](Metal_by_Tutorials_v500mpdf/6959bc249475204ea5be4438.png)

_Rotate about a point (1)_

➤ Change the code you just entered to:

`matrix = rotationMatrix * translation.inverse`

<a id="page-132"></a>

The triangle rotates by 90º around the origin.

![Figure](Metal_by_Tutorials_v500mpdf/69ecb91834a825ca113e8f15.png)

_Rotate about a point (2)_

➤ Change the code you just entered to:

`matrix = translation * rotationMatrix * translation.inverse`

Fantastic! You’re doing all of the steps of translating each vertex by the distance of the right-most vertex from the origin. After that, you’re rotating each vertex and translating it back again, causing the triangle to rotate around its right-most point.

![Figure](Metal_by_Tutorials_v500mpdf/8bdee4ee2129903420b8ec5f.png)

_Rotate about a point (3)_

<a id="page-133"></a>

## **Key Points**

• A vector is a matrix with only one row or column.

• By combining three matrices for translation, rotation and scale, you can position a model anywhere in the scene.

• In the resources folder for this chapter, references.markdown suggests further reading to help better understand transformations with linear algebra.

<a id="page-134"></a>

# 6

# Chapter 6: Coordinate Spaces

To easily find a point on a grid, you need a coordinate system. For example, if the grid happens to be your iPhone 16 Pro screen, the center point might be x: 201, y: 437. However, that point may be different depending on what space it’s in.

In the previous chapter, you learned about matrices. By multiplying a vertex’s position by a particular matrix, you can convert the vertex position to a different coordinate space. There are typically six spaces a vertex travels as its making its way through the pipeline:

• Object

• World

• Camera

• Clip

• NDC (Normalized Device Coordinate)

• Screen

Since this is starting to read like a description of Voyager leaving our solar system, let’s have a quick conceptual look at each coordinate space before attempting the conversions.

<a id="page-135"></a>

## **Object Space**

If you’re familiar with the Cartesian coordinate system, you know that it uses two points to map an object’s location. The following image shows a 2D grid with the possible vertices of the dog mapped using Cartesian coordinates.

![Figure](Metal_by_Tutorials_v500mpdf/8662eaf4a470dde6a0b5270d.png)

_Vertices in object space_

The positions of the vertices are in relation to the dog’s origin, which is located at (0, 0). The vertices in this image are located in object space (or local or model space). In the previous chapter, Triangle held an array of vertices in object space, describing the vertex of each point of the triangle.

## **World Space**

In the following image, the direction arrows mark the world’s origin at (0, 0, 0). So, in world space, the dog is at (1, 0, 1) and the cat is at (-1, 0, -2).

![Figure](Metal_by_Tutorials_v500mpdf/7e7c7904e27ad820df8a5414.png)

_Vertices in world space_

<a id="page-136"></a>

Of course, we all know that cats always see themselves at the center of the universe, so, naturally, the cat is located at (0, 0, 0) in cat space. This cat space location makes the dog’s position, (2, 0, 3), relative to the cat. When the cat moves around in his cat space, he remains at (0, 0, 0), while the position of everything else changes relative to the cat.

Note: Cat space is not recognized as a traditional 3D coordinate space, but mathematically, you can create your own space and use any position in the universe as the origin. Every other point in the universe is now relative to that origin. In a later chapter, you’ll discover other spaces besides the ones described here.

## **Camera Space**

Enough about the cat. Let’s move on to the dog. For him, the center of the universe is the person holding the camera. So, in camera space (or view space), the camera is at (0, 0, 0) and the dog is approximately at (-3, -2, 7). When the camera moves, it stays at (0, 0, 0), but the positions of the dog and cat move relative to the camera.

## **Clip Space**

The main reason for doing all this math is to project with perspective. In other words, you want to take a three-dimensional scene into a two-dimensional space. Clip space is a distorted cube that’s ready for flattening.

![Figure](Metal_by_Tutorials_v500mpdf/08e543214050ec6c7994ed0d.png)

_Clip space_

<a id="page-137"></a>

In this scene, the dog and the cat are the same size, but the dog appears smaller because of its location in 3D space. Here, the dog is farther away than the cat, so he looks smaller.

Note: If you want the dog to be its original size, you can use orthographic or isometric projection instead of perspective projection. Orthographic projection comes in handy if you’re rendering engineering drawings.

## **NDC (Normalized Device Coordinate) Space**

Projection into clip space creates a half cube of w size. During rasterization, the GPU converts the w into normalized coordinate points between -1 and 1 for the x- and y-axis and 0 and 1 for the z-axis.

## **Screen Space**

Now that the GPU has a normalized cube, it will flatten clip space into two dimensions and convert everything into screen coordinates, ready to display on the device’s screen.

In this final image, the flattened scene has perspective — with the dog being smaller than the cat, indicating the distance between the two.

![Figure](Metal_by_Tutorials_v500mpdf/b97e15f40311616c44c43102.png)

_Final render_

<a id="page-138"></a>

## **Converting Between Spaces**

To convert from one space to another, you can use transformation matrices. In the following image, the vertex on the dog’s ear is (-1, 4, 0) in object space. But in world space, the origin is different, so the vertex — judging from the image — is at about (0.75, 1.5, 1).

![Figure](Metal_by_Tutorials_v500mpdf/ba8a62a86068a6a415cb4b9c.png)

_Converting object to world_

To change the dog vertex positions from object space to world space, you can translate (move) them using a transformation matrix. Since you control four spaces, you have access to three corresponding matrices:

![Figure](Metal_by_Tutorials_v500mpdf/ad13817d88af4dfc9dc82866.png)

_The three transformation matrices_

• Model matrix: between object and world space

• View matrix: between world and camera space

• Projection matrix: between camera and clip space

## **Coordinate Systems**

Different graphics APIs use different coordinate systems. You already found out that Metal’s NDC (Normalized Device Coordinates) uses 0 to 1 on the z-axis. You also may already be familiar with OpenGL, which uses 1 to -1 on the z-axis.

In addition to being different sizes, OpenGL’s z-axis points in the opposite direction from Metal’s z-axis. That’s because OpenGL’s system is a right-handed coordinate system, and Metal’s system is a left-handed coordinate system. Both systems use x to the right and y as up.

<a id="page-139"></a>

Blender uses a different coordinate system, where `z` is up, and `y` is into the screen.

![Figure](Metal_by_Tutorials_v500mpdf/51227d03e199afdf8c5dde53.png)

_Coordinate systems_

If you’re consistent with your coordinate system and create matrices accordingly, it doesn’t matter what coordinate system you use. In this book, we’re using Metal’s left-handed coordinate system, but we could have used a right-handed coordinate system with different matrix creation methods instead.

## **The Starter Project**

With a better understanding of coordinate systems and spaces, you’re ready to start creating matrices.

➤ In Xcode, open the starter project for this chapter and build and run the app.

The project is similar to the playground you set up in Chapter 2, “3D Models”, where you rendered train.usdz.

![Figure](Metal_by_Tutorials_v500mpdf/0d38ce4adb1801f007cb27af.png)

_Starter project_

<a id="page-140"></a>

MathLibrary.swift — located in the Utility folder — contains methods that are extensions on float4x4 for creating the translation, scale and rotation matrices. This file also contains typealiases for float2/3/4, so you don’t have to type simd\_float2/3/4.

**Model.swift** contains the model initialization and loading code.

Rendering.swift has an extension on Model. You call Model.render(encoder:) from Renderer’s draw(in:) to render the model.

VertexDescriptor.swift creates a default MDLVertexDescriptor. The default MTLVertexDescriptor is derived from this descriptor. When using Model I/O to load models with vertex descriptors, the code can get a bit lengthy. Rather than creating an MTLVertexDescriptor, it’s easier to create a Model I/O MDLVertexDescriptor and then convert to the MTLVertexDescriptor that the pipeline state object needs using MTKMetalVertexDescriptorFromModelIO(\_:). If you examine the vertex descriptor code from the previous chapter, the same process is used for both vertex descriptors. You describe attributes and layouts.

At the moment, your train:

• Takes up the entire width of the screen.

• Has no depth perspective.

• Stretches to fit the size of the application window.

You can decouple the train’s vertex positions from the window size by taking the train into other coordinate spaces. The vertex function is responsible for converting the model vertices through these various coordinate spaces, and that’s where you’ll perform the matrix multiplications that do the conversions between different spaces.

## **Uniforms**

Constant values that are the same across all vertices or fragments are generally referred to as uniforms. The first step is to create a uniform structure to hold the conversion matrices. After that, you’ll apply the uniforms to every vertex.

The GPU shaders and the code on the Swift side will both access these uniform values. If you were to create a structure in Renderer and a matching structure in Shaders.metal, there’s a good chance you’ll forget to keep them synchronized. Therefore, the best approach is to create a bridging header that both C++ and Swift can access.

<a id="page-141"></a>

You’ll do that now:

➤ Using the macOS Header File template, create a new file in the Shaders folder and name it Common.h.

➤ In the Project navigator, click the main **Spaces** project folder.

➤ Select the project Spaces, and then select Build Settings along the top. Make sure All and Combined are highlighted.

➤ In the search bar, type bridg to filter the settings. Double-click the Objective-C Bridging Header value and enter Spaces/Shaders/Common.h.

![Figure](Metal_by_Tutorials_v500mpdf/21032a3799fd5c60a594bd2d.png)

_Setting up the bridging header_

This configuration tells Xcode to use this file for both the C++ derived Metal Shading Language and Swift.

➤ In **Common.h** before the final `#endif`, add the following code:

`#import <simd/simd.h>`

This code imports the simd framework, which provides types and functions for working with vectors and matrices.

➤ Next, add the uniforms structure:

```
typedef struct {
  matrix_float4x4 modelMatrix;
  matrix_float4x4 viewMatrix;
  matrix_float4x4 projectionMatrix;
} Uniforms;
```

These three matrices — each with four rows and four columns — will hold the necessary conversion between the spaces.

<a id="page-142"></a>

## **The Model Matrix**

Your train vertices are currently in object space. To convert these vertices to world space, you’ll use modelMatrix. By changing modelMatrix, you’ll be able to translate, scale and rotate your train.

➤ In Renderer.swift, add the new structure to Renderer:

`var uniforms = Uniforms()`

You defined Uniforms in Common.h (the bridging header file), so Swift is able to recognize the Uniforms type.

➤ At the bottom of `init(metalView:)`, add:

```
let translation = float4x4(translation: [0.5, -0.4, 0])
let rotation =
  float4x4(rotation: [0, 0, Float(45).degreesToRadians])
uniforms.modelMatrix = translation * rotation
```

Here, you use the matrix utility methods in MathLibrary.swift. You set modelMatrix to have a translation of 0.5 units to the right, 0.4 units down and a counterclockwise rotation of 45 degrees.

➤ In `draw(in:)` before `model.render(encoder: renderEncoder)`, add this:

```
renderEncoder.setVertexBytes(
  &uniforms,
  length: MemoryLayout<Uniforms>.stride,
  index: 11)
```

This code sets up the uniform matrix values on the Swift side.

➤ Open Shaders.metal, and import the bridging header file after setting the namespace:

`#import "Common.h"`

➤ Change the vertex function to:

```
vertex VertexOut vertex_main(
  VertexIn in [[stage_in]],
  constant Uniforms &uniforms [[buffer(11)]])
{
  float4 position = uniforms.modelMatrix * in.position;
  VertexOut out {
    .position = position
```

<a id="page-143"></a>

```
  };
  return out;
}
```

Here, you receive the Uniforms structure as a parameter, and then you multiply all of the vertices by the model matrix.

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/f4c651fbe8d4b7f953496cbf.png)

_Train in world space_

In the vertex function, you multiply the vertex position by the model matrix. All of the vertices are rotated then translated. The train vertex positions still relate to the width of the screen, so the train looks stretched. You’ll fix that momentarily.

## **View Matrix**

To convert between world space and camera space, you set a view matrix. Depending on how you want to move the camera in your world, you can construct the view matrix appropriately. The view matrix you’ll create here is a simple one, best for FPS (First Person Shooter) style games.

➤ In **Renderer.swift** at the end of `init(metalView:)`, add the following code:

`uniforms.viewMatrix = float4x4(translation: [0.8, 0, 0]).inverse`

Remember that all of the objects in the scene should move in the opposite direction to the camera. inverse does an opposite transformation. So, as the camera moves to the right, everything in the world appears to move 0.8 units to the left. With this code, you set the camera in world space, and then you add .inverse so that the objects will react in inverse relation to the camera.

<a id="page-144"></a>

➤ In **Shaders.metal**, change:

`float4 position = uniforms.modelMatrix * in.position;`

➤ To:

```
float4 position = uniforms.viewMatrix * uniforms.modelMatrix
                    * in.position;
```

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/b83d0601f02c5a330cb3a83d.png)

_Train in camera space_

The train moves 0.8 units to the left. Later, you’ll be able to navigate through a scene using the keyboard, and just changing the view matrix will update all of the objects in the scene around the camera.

The last matrix will prepare the vertices to move from camera space to clip space. This matrix will also allow you to use unit values instead of the -1 to 1 NDC (Normalized Device Coordinates) that you’ve been using. To demonstrate why this is necessary, you’ll add some animation to the train and rotate it on the y-axis.

➤ Open **Renderer.swift**, and in `draw(in:)`, just above the following code:

```
renderEncoder.setVertexBytes(
  &uniforms,
  length: MemoryLayout<Uniforms>.stride,
  index: 11)
```

<a id="page-145"></a>

➤ Add this code:

```
timer += 0.005
uniforms.viewMatrix = float4x4.identity
let translationMatrix = float4x4(translation: [0, -0.6, 0])
let rotationMatrix = float4x4(rotationY: sin(timer))
uniforms.modelMatrix = translationMatrix * rotationMatrix
```

Here, you reset the camera view matrix and replace the model matrix with a rotation around the y-axis.

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/2b36d72a39b4e20edc9b0963.png)

_A clipped train_

You can see that when the train rotates, any vertices greater than 1.0 on the z-axis are clipped. Any vertex outside Metal’s NDC will be clipped.

![Figure](Metal_by_Tutorials_v500mpdf/4972dfa675a7097a3672f971.png)

_NDC clipping_

<a id="page-146"></a>

## **Projection**

It’s time to apply some perspective to your render to give your scene some depth.

The following diagram shows a 3D scene. At the bottom-right, you can see how the rendered scene will appear.

![Figure](Metal_by_Tutorials_v500mpdf/e14aaa893b0db9be4b378b05.png)

_Projection of a scene_

When you render a scene, you need to consider:

• How much of that scene will fit on the screen. Your eyes have a field of view of about 200º, and within that field of view, your computer screen takes up about 70º.

• How far you can see by having a far plane. Computers can’t see to infinity.

• How close you can see by having a near plane.

• The aspect ratio of the screen. Currently, your train changes size when the screen size changes. When you take into account the width and height ratio, this won’t happen.

The image above shows all these things. The shape created from the near to the far plane is a cut-off pyramid called a frustum. Anything in your scene that’s located outside the frustum will not render.

<a id="page-147"></a>

Compare the rendered image again to the scene setup. The rat in the scene won’t render because he’s in front of the near plane.

MathLibrary.swift provides a projection method that returns the matrix to project objects within this frustum into clip space, ready for conversion to NDC coordinates.

## **Projection Matrix**

➤ Open Renderer.swift, and add this code to mtkView(\_:drawableSizeWillChange:):

```
let aspect =
  Float(view.bounds.width) / Float(view.bounds.height)
let projectionMatrix =
  float4x4(
    projectionFov: Float(45).degreesToRadians,
    near: 0.1,
    far: 100,
    aspect: aspect)
uniforms.projectionMatrix = projectionMatrix
```

This delegate method gets called whenever the view size changes. Because the aspect ratio will change, you must reset the projection matrix.

You’re using a field of view of 45º; a near plane of 0.1, and a far plane of 100 units.

➤ At the end of `init(metalView:)`, add this:

```
mtkView(
  metalView,
  drawableSizeWillChange: metalView.drawableSize)
```

When metalView.autoResizeDrawable is true, which is the default value, the view’s drawable size updates automatically whenever the view size changes. Any drawable textures created by the view will have this size.

This code ensures that you set up the projection matrix at the start of the app.

➤ In the vertex function of Shaders.metal, change the position matrix calculation to:

```
float4 position =
  uniforms.projectionMatrix * uniforms.viewMatrix
  * uniforms.modelMatrix * in.position;
```

<a id="page-148"></a>

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/dbde62ffc2e42ad1d7dadcd7.png)

_Zoomed in_

Because of the projection matrix, the z-coordinates measure differently now, so you’re zoomed in on the train.

➤ In **Renderer.swift** in `draw(in:)`, replace:

`uniforms.viewMatrix = float4x4.identity`

➤ With:

`uniforms.viewMatrix = float4x4(translation: [0, 0, -3]).inverse`

This moves the camera back into the scene by three units. Build and run:

![Figure](Metal_by_Tutorials_v500mpdf/45f4f41959f21683ed352ffe.png)

_Camera moved back_

<a id="page-149"></a>

➤ In mtkView(\_:drawableSizeWillChange:), change the projection matrix’s projectionFOV parameter to 70º, then build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/57b08781506e0b639947d6bb.png)

_A greater field of view_

The train appears smaller because the field of view is wider, and more objects horizontally can fit into the rendered scene.

Note: Experiment with the projection values and the model transformation. In draw(in:), set translationMatrix’s z translation value to a distance of 97, and the front of the train is just visible. At z = 98, the train is no longer visible. The projection far value is 100 units, and the camera is back 3 units. If you change the projection’s far parameter to 1000, the train is visible again.

➤ To render a solid train, in `draw(in:)`, remove:

`renderEncoder.setTriangleFillMode(.lines)`

![Figure](Metal_by_Tutorials_v500mpdf/d0e79fd00c7d00a7fd9a4ce7.png)

_The train positioned in a scene_

<a id="page-150"></a>

## **Perspective Divide**

Now that you’ve converted your vertices from object space through world space, camera space and clip space, the GPU takes over to convert to NDC coordinates (that’s -1 to 1 in the x and y directions and 0 to 1 in the z direction). The ultimate aim is to scale all the vertices from clip space into NDC space, and by using the fourth w component, that task gets a lot easier.

To scale a point, such as (1, 2, 3), you can have a fourth component: (1, 2, 3, 3). Divide by that last w component to get (1/3, 2/3, 3/3, 1). The xyz values are now scaled down. These coordinates are known as homogeneous, which means of the same kind.

The projection matrix projected the vertices from a frustum to a cube in the range -w to w. After the vertex leaves the vertex function along the pipeline, the GPU performs a perspective divide and divides the x, y and z values by their w value. The higher the w value, the further back the coordinate is. The result of this calculation is that all visible vertices will now be within NDC.

Note: To avoid a divide by zero, the projection near plane should always be a value slightly more than zero.

The w value is the main difference between a float4 vector direction and a float4 position. Because of the perspective divide, the position must have a value, generally 1, in w. Whereas a vector should have 0 in the w value as it doesn’t go through the perspective divide.

In the following picture, the dog and cat are the same height — perhaps a y value of 2, for example. With projection, since the dog is farther back, it should appear smaller in the final render.

![Figure](Metal_by_Tutorials_v500mpdf/3948dfbcedf047bcf9d39a27.png)

_The dog should appear smaller._

<a id="page-151"></a>

After projection, the cat might have a w value of ~1, and the dog might have a w value of ~8. Dividing by w would give the cat a height of 2 and the dog a height of 1/4, which will make the dog appear smaller.

## **NDC to Screen**

Finally, the GPU converts from normalized coordinates to whatever the device screen size is. You may already have done something like this at some time in your career when converting between normalized coordinates and screen coordinates.

To convert Metal NDC (Normalized Device Coordinates), which are between -1 and 1 to a device, you can use something like this:

```
converted.x = point.x * screenWidth/2  + screenWidth/2
converted.y = point.y * screenHeight/2 + screenHeight/2
```

However, you can also do this with a matrix by scaling half the screen size and translating by half the screen size. The clear advantage of this method is that you can set up a transformation matrix once and multiply any normalized point by the matrix to convert it into the correct screen space using code like this:

`converted = matrix * point`

The rasterizer on the GPU takes care of the matrix calculation for you.

## **Refactoring the Model Matrix**

Currently, you set all the matrices in Renderer. Later, you’ll create a Camera structure to calculate the view and projection matrices.

For the model matrix, rather than updating it directly, any object that you can move — such as a model or a camera — can hold a position, rotation and scale. From this information, you can construct the model matrix.

➤ In the Geometry folder, create a new Swift file named Transform.swift, and add this structure:

```
struct Transform {
  var position: float3 = [0, 0, 0]
  var rotation: float3 = [0, 0, 0]
  var scale: Float = 1
}
```

<a id="page-152"></a>

This structure will hold the transformation information for any object that you can move.

➤ Add an extension with a computed property:

```
extension Transform {
  var modelMatrix: matrix_float4x4 {
    let translation = float4x4(translation: position)
    let rotation = float4x4(rotation: rotation)
    let scale = float4x4(scaling: scale)
    let modelMatrix = translation * rotation * scale
    return modelMatrix
  }
}
```

This code automatically creates a model matrix from any transformable object.

➤ Add a new protocol so that you can mark objects as transformable:

```
protocol Transformable {
  var transform: Transform { get set }
}
```

➤ Because it’s a bit longwinded to type model.transform.position, add a new extension to Transformable:

```
extension Transformable {
  var position: float3 {
    get { transform.position }
    set { transform.position = newValue }
  }
  var rotation: float3 {
    get { transform.rotation }
    set { transform.rotation = newValue }
  }
  var scale: Float {
    get { transform.scale }
    set { transform.scale = newValue }
  }
}
```

This code provides computed properties to allow you to use model.position directly, and the model’s transform will update from this value.

➤ Open Model.swift, and mark Model as Transformable.

`class Model: Transformable {`

<a id="page-153"></a>

➤ Add the new transform property to Model:

`var transform = Transform()`

➤ Open **Renderer.swift**, and from `init(metalView:)`, remove:

```
let translation = float4x4(translation: [0.5, -0.4, 0])
let rotation =
  float4x4(rotation: [0, 0, Float(45).degreesToRadians])
uniforms.modelMatrix = translation * rotation
uniforms.viewMatrix = float4x4(translation: [0.8, 0, 0]).inverse
```

You’ll set these matrices in draw(in:).

➤ In `draw(in:)`, replace:

```
let translationMatrix = float4x4(translation: [0, -0.6, 0])
let rotationMatrix = float4x4(rotationY: sin(timer))
uniforms.modelMatrix = translationMatrix * rotationMatrix
```

➤ With:

```
model.position.y = -0.6
model.rotation.y = sin(timer)
uniforms.modelMatrix = model.transform.modelMatrix
```

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/c548dcdacb45fa593ccd7b0f.png)

_Using a transform in Model_

The result is exactly the same, but the code is much easier to read — and changing a model’s position, rotation and scale is more accessible. Later, you’ll extract this code into a GameScene so that Renderer is left only to render models rather than manipulate them.

<a id="page-154"></a>

## **Key Points**

• Coordinate spaces map different coordinate systems. To convert from one space to another, you can use matrix multiplication.

• Model vertices start off in object space. These are generally held in the file that comes from your 3D app, such as Blender, but you can procedurally generate them too.

• The model matrix converts object space vertices to world space. These are the positions that the vertices hold in the scene’s world. The origin at [0, 0, 0] is the center of the scene.

• The view matrix moves vertices into camera space. Generally, your matrix will be the inverse of the position of the camera in world space.

• The projection matrix applies three-dimensional perspective to your vertices.

## **Where to Go From Here?**

You’ve covered a lot of mathematical concepts in this chapter without diving too far into the underlying mathematical principles. To get started in computer graphics, you can fill your transform matrices and continue multiplying them at the usual times, but to be sufficiently creative, you’ll need to understand some linear algebra. A great place to start is Grant Sanderson’s Essence of Linear Algebra at https://bit.ly/ 3iYnkN1. This video treats vectors and matrices visually. You’ll also find some additional references in references.markdown in the resources folder for this chapter.

<a id="page-155"></a>

# 7

# Chapter 7: The Fragment Function

Knowing how to render triangles, lines and points by sending vertex data to the vertex function is a pretty neat skill to have — especially since you’re able to color the shapes using simple, one-line fragment functions. However, fragment shaders are capable of doing a lot more.

➤ Browse the website https://shadertoy.com, where you’ll find a dizzying number of brilliant community-created shaders.

![Figure](Metal_by_Tutorials_v500mpdf/355fd88a1d877e58b9989349.png)

_shadertoy.com examples_

Some of these examples may look like renderings of complex 3D models, but looks are deceiving! Every “model” is entirely generated using mathematics, written in a GLSL fragment shader. GLSL is the Graphics Library Shading Language for OpenGL — and in this chapter, you’ll begin to understand the principles that all shading masters use.

<a id="page-156"></a>

Note: Every graphics API uses its own shader language. The principles are the same, so if you find a GLSL shader you like, you can recreate it in Metal’s MSL.

## **The Starter Project**

The starter project shows an example of using multiple pipeline states with different vertex functions, depending on whether you render the rotating train or the full-screen quad.

➤ Open the starter project for this chapter.

➤ Build and run the project. (You can choose to render the train or the quad. You’ll start with the quad first.)

![Figure](Metal_by_Tutorials_v500mpdf/bcbe999f426b15e3b861b96f.png)

_The starter project_

Let’s have a closer look at the code.

➤ Open **Vertex.metal** in the **Shaders** group, and you’ll see two vertex functions:

• vertex\_main: This function renders the train, just as it did in the previous chapter.

• vertex\_quad: This function renders the full-screen quad using an array defined in the shader.

<a id="page-157"></a>

Both functions output a `VertexOut`, containing only the vertex’s position.

➤ Open Renderer.swift.

In init(metalView:options:), you’ll see two pipeline state objects (PSOs). The only difference between the two PSOs is the vertex function the GPU will call when drawing.

Depending on the value of options.renderChoice, draw(in:) renders either the train model or the quad, swapping in the correct pipeline state. The SwiftUI views handle updating Options and MetalView passes the current option to Renderer.

➤ Ensure you understand how this project works before you continue.

## **Screen Space**

One of the many things a fragment function can do is create complex patterns that fill the screen on a rendered quad. At the moment, the fragment function has only the interpolated position output from the vertex function available to it. So first, you’ll learn what you can do with this position and what its limitations are.

➤ Open **Fragment.metal**, and change the fragment function contents to:

```
float color;
in.position.x < 200 ? color = 0 : color = 1;
return float4(color, color, color, 1);
```

When the rasterizer processes the vertex positions, it converts them from NDC (Normalized Device Coordinates) into screen space. You defined the width of the Metal view in ContentView.swift as 400 points. With the newly added code, you say that if the x position is less than 200, make the color black. Otherwise, make the color white.

Note: Although you can use an if statement, the compiler optimizes the ternary statement better, so it makes more sense to use that instead.

<a id="page-158"></a>

➤ Build and run the app on both your Mac and iPhone 16 Pro Max Simulator.

![Figure](Metal_by_Tutorials_v500mpdf/6c452ac4e4c72bebaff51fcf.png)

_MacBook Pro vs iPhone 15 Pro Max_

Did you expect half the screen to be black? The view is 400 points wide, so it would make sense. But there’s something you might not have considered: Apple Retina displays have various pixel resolutions or pixel densities. For example, a MacBook Pro has a 2x Retina display, whereas the iPhone 16 Pro Max has a 3x Retina display. These different displays mean that the 400 point Metal view on a MacBook Pro creates an 800x800 pixel drawable texture and the iPhone view creates a 1200x1200 pixel drawable texture.

Your quad fills up the screen, and you’re writing to the view’s drawable render target texture (the size of which matches the device’s display), but there’s no easy way to find out in the fragment function what size the current render target texture is.

➤ Open **Common.h**, and add a new structure:

```
typedef struct {
  uint32_t width;
  uint32_t height;
} Params;
```

This code holds parameters that you can send to the fragment function. You can add parameters to this structure as you need them. width and height are 32-bit unsigned integers.

➤ Open Renderer.swift, and add a new property to Renderer:

`var params = Params()`

<a id="page-159"></a>

You’ll store the current render target size in the new property.

➤ Add the following code to the end of mtkView(\_:drawableSizeWillChange:):

```
params.width = UInt32(size.width)
params.height = UInt32(size.height)
```

size contains the drawable texture size of the view. In other words, the view’s bounds scaled by the device’s scale factor.

➤ In draw(in:), before calling the methods to render the model or quad, send the parameters to the fragment function:

```
renderEncoder.setFragmentBytes(
  &params,
  length: MemoryLayout<Params>.stride,
  index: 12)
```

Notice that you’re using setFragmentBytes(\_:length:index:) to send data to the fragment function the same way you previously used setVertexBytes(\_:length:index:).

➤ Open **Fragment.metal**, and change the signature of `fragment_main` to:

```
fragment float4 fragment_main(
  constant Params &params [[buffer(12)]],
  VertexOut in [[stage_in]])
```

Params with the target drawing texture size is now available to the fragment function.

➤ Change the code that sets the value of color — based on the value of in.position.x — to:

`in.position.x < params.width * 0.5 ? color = 0 : color = 1;`

Here, you’re using the target render size for the calculation.

➤ Run the app in both macOS and iPhone 16 Pro Max Simulator.

<a id="page-160"></a>

Fantastic, the render now looks the same for both devices.

![Figure](Metal_by_Tutorials_v500mpdf/1624fbfe84dce708bc170927.png)

_Corrected for retina devices_

## **Metal Standard Library Functions**

In addition to standard mathematical functions such as sin, abs and length, there are a few other useful functions. Let’s have a look.

## **step**

step(edge, x) returns 0 if x is less than edge. Otherwise, it returns 1. This evaluation is exactly what you’re doing with your current fragment function.

➤ Replace the contents of the fragment function with:

```
float color = step(params.width * 0.5, in.position.x);
return float4(color, color, color, 1);
```

This code produces the same result as before but with slightly less code.

➤ Build and run.

![Figure](Metal_by_Tutorials_v500mpdf/cd7c727b9ac90730f8c3759c.png)

_step_

The result is that you get black on the left where the result of step is 0, and white on the right where the result of step is 1.

<a id="page-161"></a>

Let’s take this further with a checkerboard pattern.

➤ Replace the contents of the fragment function with:

```
uint32_t checks = 8;
// 1
float2 uv = in.position.xy / params.width;
// 2
uv = fract(uv * checks * 0.5) - 0.5;
// 3
float3 color = step(uv.x * uv.y, 0.0);
return float4(color, 1.0);
```

Here’s what’s happening:

1. UV coordinates form a grid with values between 0 and 1. The mid-point, therefore, is at [0.5, 0.5], with the top left at [0.0, 0.0]. UV coordinates are most often associated with mapping vertices to textures, as you’ll see in Chapter 8, “Textures”.

2. fract(x) returns the fractional part of x. You take the fractional value of the UVs multiplied by half the number of checks, which gives you a value between 0 and 1. You then subtract 0.5 so that half the values are less than zero.

3. If the result of the xy multiplication is less than zero, the result is 1 or white. Otherwise, it’s 0 or black.

For example:

```
float2 uv = float2(550, 50) / 800;     // uv = (0.6875, 0.0625)
uv = fract(uv * checks * 0.5);   // uv = (0.75, 0.25)
uv -= 0.5; // uv = (0.25, -0.25)
float3 color = step(uv.x * uv.y, 0.0); // x > -0.0625, so color
is 1
```

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/de30eca774e4ea69a2c20220.png)

_Checker board_

<a id="page-162"></a>

## **length**

Creating squares is a lot of fun, but let’s create some circles using a length function.

➤ Replace the fragment function with:

```
float center = 0.5;
float radius = 0.2;
float2 uv = in.position.xy / params.width - center;
float3 color = step(length(uv), radius);
return float4(color, 1.0);
```

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/36ed83f32d3a32974240f0df.png)

_Circle_

To resize and move the shape around the screen, you change the circle’s center and radius.

## **smoothstep**

smoothstep(edge0, edge1, x) returns a smooth Hermite interpolation between 0 and 1.

Note: edge1 must be greater than edge0, and x should be edge0 &lt;= x &lt;= edge1.

<a id="page-163"></a>

➤ Change the fragment function to:

```
float color = smoothstep(0, params.width, in.position.x);
return float4(color, color, color, 1);
```

color contains a value between 0 and 1. When the position is the same as the screen width, the color is 0 or white. When the position is at the very left of the screen, the color is 0 or black.

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/407c9fe468de88d2dab13515.png)

_smoothstep gradient_

Between the two edge cases, the color is a gradient interpolating between black and white. Here, you use smoothstep to calculate a color, but you can also use it to interpolate between any two values. For example, you can use smoothstep to animate a position in the vertex function.

## **mix**

mix(x, y, a) produces the same result as x + (y - x) \* a.

➤ Change the fragment function to:

```
float3 red = float3(1, 0, 0);
float3 blue = float3(0, 0, 1);
float3 color = mix(red, blue, 0.6);
return float4(color, 1);
```

A mix of 0 produces full red. A mix of 1 produces full blue. Together, these colors produce a 60% blend between red and blue.

<a id="page-164"></a>

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/61da0114c3ef36c47aa53b36.png)

_A blend between red and blue_

You can combine `mix` with `smoothstep` to produce a color gradient.

➤ Replace the fragment function with:

```
float3 red = float3(1, 0, 0);
float3 blue = float3(0, 0, 1);
float result = smoothstep(0, params.width, in.position.x);
float3 color = mix(red, blue, result);
return float4(color, 1);
```

This code takes the interpolated result and uses it as the amount to mix red and blue.

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/ab0db832ebfd037de6b44c84.png)

_Combining smoothstep and mix_

<a id="page-165"></a>

## **normalize**

The process of normalization means to rescale data to use a standard range. For example, a vector has both direction and magnitude. In the following image, vector A has a length of 2.12132 and a direction of 45 degrees. Vector B has the same length but a different direction. Vector C has a different length but the same direction.

![Figure](Metal_by_Tutorials_v500mpdf/e3a35f134ff7669bb5cec927.png)

_Vectors_

It’s easier to compare the direction of two vectors if they have the same magnitude, so you normalize the vectors to a unit length. normalize(x) returns the vector x in the same direction but with a length of 1.

Let’s look at another example of normalizing. Say you want to visualize the vertex positions using colors so that you can better debug some of your code.

➤ Change the fragment function to:

`return in.position;`

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/9945de6e4d7a421e7b233511.png)

_Visualizing positions_

<a id="page-166"></a>

The fragment function should return an RGBA color with each element between 0 and 1. However, because the position is in screen space, each position varies between [0, 0, 0] and [800, 800, 0], which is why the quad renders yellow (it’s only between 0 and 1 at the top-left corner).

➤ Now, change the code to:

```
float3 color = normalize(in.position.xyz);
return float4(color, 1);
```

Here, you normalize the vector in.position.xyz to have a length of 1. All of the colors are now guaranteed to be between 0 and 1. When normalized, the position (800, 0, 0) at the far top-right contains 1, 0, 0, which is red.

➤ Build and run the app to see the result.

![Figure](Metal_by_Tutorials_v500mpdf/a436ce0260801fa5da333f25.png)

_Normalized positions_

## **Normals**

Although visualizing positions is helpful for debugging, it’s not generally helpful in creating a 3D render. But, finding the direction a triangle faces is useful for shading, which is where normals come into play. Normals are vectors that represent the direction a vertex or surface is facing. In the next chapter, you’ll learn how to light your models. But first, you need to understand normals.

<a id="page-167"></a>

The following image captured from Blender shows vertex normals pointing out. Each of the sphere’s vertices points in a different direction.

![Figure](Metal_by_Tutorials_v500mpdf/c1c48040c48e83b894fcdf0f.png)

_Vertex normals_

The shading of the sphere depends upon these normals. If a normal points toward the light source, Blender will shade brighter.

A quad isn’t very interesting for shading purposes, so switch the default render to the train.

➤ Open **Options.swift**, and change the initialization of `renderChoice` to:

`var renderChoice = RenderChoice.train`

➤ Run the app to check your train render.

![Figure](Metal_by_Tutorials_v500mpdf/d863213d083b61d499542562.png)

_Train render_

Unlike the full-screen quad, only fragments covered by the train will render. The color of each fragment, however, is still dependent upon the fragment’s screen position and not the position or direction of the train vertices.

<a id="page-168"></a>

## **Loading the Train Model With Normals**

3D model files generally contain surface normal values, and you can load these values with your model. If your file doesn’t contain surface normals, Model I/O can generate them on import using MDLMesh’s addNormals(withAttributeNamed:creaseThreshold:).

## **Adding Normals to the Vertex Descriptor**

➤ Open VertexDescriptor.swift.

At the moment, you load only the position attribute. It’s time to add the normal to the vertex descriptor.

➤ After the code that sets up offset, and before the code that sets layouts[0], add the following code to MDLVertexDescriptor’s defaultLayout:

```
vertexDescriptor.attributes[1] = MDLVertexAttribute(
  name: MDLVertexAttributeNormal,
  format: .float3,
  offset: offset,
  bufferIndex: 0)
offset += MemoryLayout<float3>.stride
```

Here, a normal is a float3, and interleaved with the position in buffer 0. float3 is a typealias of SIMD3&lt;Float&gt; defined in MathLibrary.swift. Each vertex takes up two float3s, which is 32 bytes, in buffer index 0. layouts[0] describes buffer index 0 with the stride.

## **Updating the Shader Functions**

➤ Open Vertex.metal.

The pipeline state for the train model uses this vertex descriptor so that the vertex function can process the attributes, and you match the attributes with those in VertexIn.

➤ Build and run the app, and you’ll see that everything still works as expected.

Even though you added a new attribute to the vertex buffer, the pipeline ignores it since you haven’t included it as an attribute(n) in VertexIn. Time to fix that.

<a id="page-169"></a>

➤ Add the following code to VertexIn:

`float3 normal [[attribute(1)]];`

Here, you match attribute(1) with the vertex descriptor’s attribute 1. So now you’ll be able to access the normal attribute in the vertex function.

➤ Next, add the following code to VertexOut:

`float3 normal;`

By including the normal here, you can now pass the data on to the fragment function.

➤ In vertex\_main, change the assignment to out:

```
VertexOut out {
  .position = position,
  .normal = in.normal
};
```

Perfect! With that change, you can now return both the position and the normal from the vertex function.

➤ Open **Fragment.metal**, and replace the contents of `fragment_main` with:

`return float4(in.normal, 1);`

Don’t worry, that compile error is expected. Even though you updated VertexOut in Vertex.metal, the scope of that structure was only in that one file.

## **Adding a Header**

It’s common to require structures and functions in multiple shader files. So, just as you did with the bridging header Common.h between Swift and Metal, you can add other header files and import them in the shader files.

➤ Create a new file in the Shaders group using the macOS Header File template, and name it ShaderDefs.h.

➤ Replace the code with:

```
#include <metal_stdlib>
using namespace metal;

struct VertexOut {
```

<a id="page-170"></a>

```
  float4 position [[position]];
  float3 normal;
};
```

Here, you define `VertexOut` within the `metal` namespace.

➤ Open **Vertex.metal**, and delete the `VertexOut` structure.

➤ After importing **Common.h**, add:

`#import "ShaderDefs.h"`

➤ Open **Fragment.metal**, and delete the `VertexOut` structure.

➤ Again, after importing **Common.h**, add:

`#import "ShaderDefs.h"`

➤ Build and run the app.

Oh, now that looks a little odd!

![Figure](Metal_by_Tutorials_v500mpdf/d8075f0c11acf75aa55a2053.png)

_Normals with rendering weirdness_

Your normals appear as if they are displaying correctly — red normals are at the train’s right, green is up and blue is at the back — but as the train rotates, parts of it seem almost transparent.

The problem here is that the rasterizer is jumbling up the depth order of the vertices. When you look at a train from the front, you shouldn’t be able to see the back of the train; it should be occluded.

<a id="page-171"></a>

## **Depth**

The rasterizer doesn’t process depth order by default, so you need to give the rasterizer the information it needs with a depth stencil state.

As you may remember from Chapter 3, “The Rendering Pipeline”, the Stencil Test checks whether fragments are visible after the fragment function, during the rendering pipeline. If a fragment is determined to be behind another fragment, it’s discarded.

Let’s give the render encoder an MTLDepthStencilState property to describe how to do this testing.

➤ Open Renderer.swift.

➤ Toward the end of init(metalView:options:), after setting metalView.clearColor, add:

`metalView.depthStencilPixelFormat = .depth32Float`

This code tells the view that it needs to hold the depth information. The default pixel format is .invalid, which informs the view that it doesn’t need to create a depth and stencil texture.

The pipeline state that the render command encoder uses has to have the same depth pixel format.

➤ In init(metalView:options:), after setting pipelineDescriptor.colorAttachments[0].pixelFormat, before do {, add:

`pipelineDescriptor.depthAttachmentPixelFormat = .depth32Float`

If you were to build and run the app now, you’d get the same result as before. However, behind the scenes, the view creates a texture to which the rasterizer can write depth values.

Next, you need to set how you want the rasterizer to calculate your depth values.

➤ Add a new property to Renderer:

`let depthStencilState: MTLDepthStencilState?`

This property holds the depth stencil state with the correct render settings.

<a id="page-172"></a>

➤ Create this method in `Renderer` to instantiate the depth stencil state:

```
static func buildDepthStencilState() -> MTLDepthStencilState? {
// 1
  let descriptor = MTLDepthStencilDescriptor()
// 2
  descriptor.depthCompareFunction = .less
// 3
  descriptor.isDepthWriteEnabled = true
  return Renderer.device.makeDepthStencilState(
    descriptor: descriptor)
}
```

Going through this code:

1. Create a descriptor that you’ll use to initialize the depth stencil state, just as you did the pipeline state objects.

2. Specify how to compare the current and already processed fragments. With a compare function of less, if the current fragment depth is less than the depth of the previous fragment in the framebuffer, the current fragment replaces that previous fragment.

3. State whether to write depth values. If you have multiple passes, as you will in Chapter 12, “Render Passes”, sometimes you’ll want to read the already drawn fragments. In that case, set isDepthWriteEnabled to false. Note that isDepthWriteEnabled is always true when you’re drawing objects that require depth.

➤ Call the method from init(metalView:options:) before super.init():

`depthStencilState = Self.buildDepthStencilState()`

➤ In draw(in:), add this to the top of the method after guard { }:

`renderEncoder.setDepthStencilState(depthStencilState)`

➤ Build and run the app to see your train in glorious 3D.

<a id="page-173"></a>

As the train rotates, it appears in shades of red, green, blue and black.

![Figure](Metal_by_Tutorials_v500mpdf/5921824b60e36c0b1a94e865.png)

_Normals_

Consider what you see in this render. The normals are currently in object space. So, even though the train rotates in world space, the colors/normals don’t change as the model changes its rotation.

![Figure](Metal_by_Tutorials_v500mpdf/33457002083fb48c5e5f7d29.png)

_Normal colors along axes_

When a normal points to the right along the model’s x-axis, the value is [1, 0, 0]. That’s the same as red in RGB values, so the fragment is colored red for those normals pointing to the right.

The normals pointing upwards are 1 on the y-axis, so the color is green.

<a id="page-174"></a>

The normals pointing toward the camera are negative. They’re black when a color is [0, 0, 0] or less. When you see the back of the train as it rotates, you can just make out that the back of the wheels pointing in the z direction are blue [0, 0, 1].

Now that you have normals in the fragment function, you can start manipulating colors depending on the direction they’re facing. Manipulating colors is important when you start playing with lighting.

## **Hemispheric Lighting**

Hemispheric lighting uses ambient light. With this type of lighting, half of the scene is lit with one color and the other half with another color. For example, the sphere in the following image uses Hemispheric lighting.

![Figure](Metal_by_Tutorials_v500mpdf/48bef8c285793d7e96bd081b.png)

_Hemispheric lighting_

Notice how the sphere appears to take on the color reflected from the sky (top) and the color reflected from the ground (bottom). To see this type of lighting in action, you’ll change the fragment function so that:

• Normals facing up are blue.

• Normals facing down are green.

• Interim values are a blue and green blend.

<a id="page-175"></a>

➤ Open **Fragment.metal**, and replace the contents of `fragment_main` with:

```
float4 sky = float4(0.34, 0.9, 1.0, 1.0);
float4 earth = float4(0.29, 0.58, 0.2, 1.0);
float intensity = in.normal.y * 0.5 + 0.5;
return mix(earth, sky, intensity);
```

mix(x, y, z) interpolates between the first two values depending on the third value, which must be between 0 and 1. Your normal values are between -1 and 1, so you convert the intensity between 0 and 1.

➤ Build and run the app to see your lit train. Notice how the top of the train is blue and its underside is green.

![Figure](Metal_by_Tutorials_v500mpdf/dd7aad4fb151519bd007bc78.png)

_Hemispheric lighting_

Fragment shaders are powerful, allowing you to color objects with precision. In Chapter 10, “Lighting Fundamentals”, you’ll use the power of normals to shade your scene with more realistic lighting. In Chapter 19, “Tessellation &amp; Terrains”, you’ll create a similar effect to this one as you learn how to place snow on a terrain depending on the slope.

<a id="page-176"></a>

## **Challenge**

Currently, you’re using hard-coded magic numbers for all of the buffer indices and attributes. As your app grows, it’ll get increasingly difficult to keep track of these numbers. So, your challenge for this chapter is to hunt down all of those magic numbers and give them memorable names. For this challenge, you’ll create an enum in Common.h.

Here’s some code to get you started:

```
typedef enum {
  VertexBuffer = 0,
  UniformsBuffer = 11,
  ParamsBuffer = 12
} BufferIndices;
```

You can now use these constants in both Swift and C++ shader functions:

```
//Swift
encoder.setVertexBytes(
  &uniforms,
  length: MemoryLayout<Uniforms>.stride,
  index: Int(UniformsBuffer.rawValue))

// Shader Function
vertex VertexOut vertex_main(
  const VertexIn in [[stage_in]],
  constant Uniforms &uniforms [[buffer(UniformsBuffer)]])
```

You can even add an extension in **VertexDescriptor.swift** to prettify the code:

```
extension BufferIndices {
  var index: Int {
    return Int(self.rawValue)
  }
}
```

With this code, you can use UniformsBuffer.index instead of Int(UniformsBuffer.rawValue).

You’ll find the full solution in the challenge folder for this chapter.

<a id="page-177"></a>

## **Key Points**

• The fragment function is responsible for returning a color for each fragment that successfully passes through the rasterizer and the Depth / Stencil Test.

• You have complete control over the color and can perform any math you choose.

• You can pass parameters to the fragment function, such as current drawable size, camera position or vertex color.

• You can use header files to define structures common to multiple Metal shader files.

• Check the Metal Shading Language Specification at https://apple.co/3jDLQn4 for all of the MSL functions available in shader functions.

• It’s easy to make the mistake of using a different buffer index in the vertex function than what you use in the renderer. Use descriptive enumerations for buffer indices.

## **Where to Go From Here?**

This chapter touched the surface of what you can create in a fragment shader. SwiftUI’s Shader allows you to run a fragment shader on the contents of a SwiftUI view. Instead of having to write a complete Metal app, you can simply create a SwiftUI Image View and test your shadercraft.

Paul Hudson (twostraws) has written a magnificent open-source collection of shaders that you can download from https://github.com/twostraws/Inferno.

<a id="page-178"></a>

# 8

# Chapter 8: Textures

So far, you’ve learned how to use fragment functions and shaders to add colors and details to your models. Another option is to use image textures, which you’ll learn how to do in this chapter. More specifically, you’ll learn about:

• UV coordinates: How to unwrap a mesh so that you can apply a texture to it.

• Texturing a model: How to read the texture in a fragment shader.

• Asset catalog: How to organize your textures.

• Samplers: Different ways you can read (sample) a texture.

• Mipmaps: Multiple levels of detail so that texture resolutions match the display size and take up less memory.

<a id="page-179"></a>

## **Textures and UV Maps**

The following image shows a house model with twelve vertices. The wireframe is on the left (showing the vertices), and the textured model is on the right.

![Figure](Metal_by_Tutorials_v500mpdf/f52296ab44c9803c31d68a24.png)

_A low poly house_

Note: If you want a closer look at this model, you’ll find the Blender and texture files in the resources/LowPolyHouse folder for this chapter.

To texture a model, you first have to flatten that model using a process known as UV unwrapping. UV unwrapping creates a UV map by unfolding the model. To unfold the model, you mark and cut seams using a modeling app. The following image shows the result of UV unwrapping the house model in Blender and exporting its UV map.

![Figure](Metal_by_Tutorials_v500mpdf/05b4167340b97b04a22deed1.png)

_The house UV map_

<a id="page-180"></a>

Notice that the roof and walls have marked seams. Seams are what make it possible for this model to lie flat. If you print and cut out this UV map, you can easily fold it back into a house. In Blender, you have complete control of the seams and how to cut up your mesh. Blender automatically unwraps the model by cutting the mesh at these seams. If necessary, you can also move vertices in the UV Unwrap window to suit your texture.

Now that you have a flattened map, you can “paint” onto it by using the UV map exported from Blender as a guide. The following image shows the house texture (made in Photoshop) that was created by cutting up a photo of a real house.

![Figure](Metal_by_Tutorials_v500mpdf/09a62ba0100d58ad889a10c9.png)

_Low poly house color texture_

Note how the edges of the texture aren’t perfect, and the copyright message is visible. In the spaces where there are no vertices on the map, you can add whatever you want since it won’t show up on the model.

Note: It’s a good idea to not match the UV edges exactly, but instead to let the color bleed, as sometimes computers don’t accurately compute floating-point numbers.

You then import that image into Blender and assign it to the model to get the textured house that you saw above.

<a id="page-181"></a>

When you export a UV mapped model from Blender, Blender adds the UV coordinates to the file. Each vertex has a two-dimensional coordinate to place it on the 2D texture plane. The top-left is (0, 1) and the bottom-right is (1, 0).

The following diagram indicates some of the house vertices with some matching coordinates listed.

![Figure](Metal_by_Tutorials_v500mpdf/e74bc48eb837d3d481e35a59.png)

_UV coordinates_

One of the advantages of mapping from 0 to 1 is that you can swap in lower or higher resolution textures. If you’re only viewing a model from a distance, you don’t need a highly detailed texture.

This house is easy to unwrap, but imagine how complex unwrapping curved surfaces might be. The following image shows a UV map of the train (which is still a simple model):

![Figure](Metal_by_Tutorials_v500mpdf/a4f4384c217d80753fd9f56e.png)

_The train's UV map_

<a id="page-182"></a>

Photoshop, naturally, is not the only solution for texturing a model. You can use any image editor for painting on a flat texture. In the last few years, several other apps that allow painting directly on the model have become mainstream, such as:

• Blender (free)

• Procreate on iPad ($)

• Substance Designer and Substance Painter by Adobe ($$): In Designer, you can create complex materials procedurally. Using Substance Painter, you can paint these materials on the model.

• 3DCoat by 3Dcoat.com ($$)

• Mari by Foundry ($$$)

In addition to texturing, using Blender, 3DCoat or Nomad Sculpt on iPad, you can sculpt models in a similar fashion to ZBrush and then remesh the high poly sculpt to create a low poly model. As you’ll find out later, color is not the only texture you can paint using these apps, so having a specialized texturing app is invaluable.

## **The Starter App**

➤ Open the starter project for this chapter, and build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/07a12dadb7d5b1d7075243a1.png)

_The starter app_

<a id="page-183"></a>

The scene contains the low poly house. The fragment shader code is the same code from the challenge in the previous chapter, with hemispheric lighting added and a different background clear color.

The other major changes are:

• Mesh.swift and Submesh.swift extract the Model I/O and MetalKit mesh buffers into custom vertex buffers and submesh groups. Model now contains an array of Meshs in place of a single MTKMesh. Abstracting away from the Metal API allows for greater flexibility when generating models that don’t use Model I/O and MetalKit. Remember, it’s your engine, so you can choose how to hold the mesh data.

• Primitive.swift extends Model so that you can render primitive shapes easily. The file allows a plane and a sphere, but you could add other primitive shapes.

• VertexDescriptor.swift contains a UV attribute in addition to Position and Normal attributes. Model loads UVs in the same way as you loaded normals in the previous chapter. Notice how the UVs will go into a separate buffer from the position and normal. This isn’t necessary, but it makes the layout more flexible for use with custom-generated models.

• Renderer.swift passes uniforms and params to Model to perform the rendering code.

• ShaderDefs.h contains VertexIn and VertexOut. These structures have an additional uv property. vertex\_main passes the interpolated UV to the fragment function.

In this chapter, you’ll replace the sky and earth colors in the fragment function with colors from the texture. Initially, you’ll use the texture included in lowpoly-house.usdz,  located in the Assets folder. To read the texture in the fragment function, you’ll take the following steps:

1. Load and store the image texture centrally.

2. Pass the loaded texture to the fragment function before drawing the model.

3. Change the fragment function to read the appropriate pixel from the texture.

<a id="page-184"></a>

## **1. Loading the Texture**

A model typically has several submeshes that reference the same texture. Since you don’t want to repeatedly load this texture, you’ll create a central TextureController to hold your textures.

➤ Create a new folder called Textures under the Texture folder, and in this folder, create a new Swift file named TextureController.swift. Replace the code with:

```
import MetalKit

enum TextureController {
  static var textures: [String: MTLTexture] = [:]
}
```

TextureController will grab the textures used by your models and hold them in this dictionary.

➤ Add a new method to TextureController:

```
static func loadTexture(texture: MDLTexture, name: String) ->
MTLTexture? {
  // 1
  if let texture = textures[name] {
    return texture
  }
  // 2
  let textureLoader = MTKTextureLoader(device: Renderer.device)
  // 3
  let textureLoaderOptions: [MTKTextureLoader.Option: Any] =
    [.origin: MTKTextureLoader.Origin.bottomLeft]
  // 4
  let texture = try? textureLoader.newTexture(
    texture: texture,
    options: textureLoaderOptions)
  print("loaded texture from USD file")
  // 5
  textures[name] = texture
  return texture
}
```

This method will receive a Model I/O texture and return a MetalKit texture ready for rendering.

<a id="page-185"></a>

Going through the code:

1. If the texture has already been loaded into textures, return it. Note that you’re loading the texture by name, so your artists must ensure that the models’ textures don’t have conflicting names.

2. Create a texture loader using MetalKit’s MTKTextureLoader.

3. Change the texture’s origin option to ensure that the texture loads with its origin at the bottom-left. Without this option, the texture won’t wrap the house correctly.

4. Create a new MTLTexture using the provided texture and loader options. For debugging purposes, print a message.

5. Add the texture to textures and return it.

Note: Loading textures can get complicated. When Metal was first released, you had to specify everything about the image, such as pixel format, dimensions and usage, using MTLTextureDescriptor. However, with MetalKit’s MTKTextureLoader, you can use the provided default values and optionally change them as needed.

## **Loading the Submesh Texture**

Each submesh of a model’s mesh has a different material characteristic, such as roughness, base color and metallic content. For now, you’ll focus only on the base color texture. In Chapter 11, “Maps &amp; Materials”, you’ll look at some of the other characteristics. Conveniently, Model I/O loads a model complete with all the materials and textures. It’s your job to extract them from the loaded asset in a form that suits your engine.

➤ Open Model.swift, and locate let asset = MDLAsset.... After this line, add this:

`asset.loadTextures()`

Model I/O will add MDLTextureSampler values to the submeshes, so you’ll be able to load the textures shortly.

<a id="page-186"></a>

➤ Open Submesh.swift, and inside Submesh, create a structure and a property to hold the textures:

```
struct Textures {
  var baseColor: MTLTexture?
}

var textures: Textures
```

Don’t worry about compile errors; your project won’t compile until you’ve initialized textures.

MDLSubmesh holds each submesh’s material information in an MDLMaterial property. You provide the material with a semantic to retrieve the value for the relevant material. For example, the semantic for base color is MDLMaterialSemantic.baseColor.

➤ At the end of **Submesh.swift**, add three new extensions:

```
// 1
private extension Submesh.Textures {
  init(material: MDLMaterial?) {
    baseColor = material?.texture(type: .baseColor)
  }
}

// 2
private extension MDLMaterialProperty {
  var textureName: String {
    stringValue ?? UUID().uuidString
  }
}

// 3
private extension MDLMaterial {
  func texture(type semantic: MDLMaterialSemantic) ->
MTLTexture? {
    if let property = property(with: semantic),
    property.type == .texture,
    let mdlTexture = property.textureSamplerValue?.texture {
      return TextureController.loadTexture(
        texture: mdlTexture,
        name: property.textureName)
    }
    return nil
  }
}
```

<a id="page-187"></a>

Going through what these extensions do:

1. Load up the base color (diffuse) texture with the provided submesh material. Later, you’ll load other textures for the submesh in the same way.

2. MDLMaterialProperty.textureName returns either the texture name in the file or a unique identifier when no name is provided.

3. MDLMaterial.property(with:) looks up the provided property in the submesh’s material. You then check whether the property type is a texture and load the texture into TextureController.textures. Material properties can also be float values where there is no texture available for the submesh.

➤ At the bottom of `init(mdlSubmesh:mtkSubmesh)` add:

`textures = Textures(material: mdlSubmesh.material)`

You initialize the submesh textures and finally remove the compiler warning.

➤ Build and run your app to check that everything’s working. Your model will look the same as in the initial screenshot. However, you’ll get a message in the console: loaded texture from USD file, showing that the texture loader has successfully loaded the house’s texture.

![Figure](Metal_by_Tutorials_v500mpdf/78cb03cdb61f874fbb5e7b7a.png)

_The render hasn't changed_

<a id="page-188"></a>

## 2. Passing the Loaded Texture to the Fragment Function

In a later chapter, you’ll learn about several other texture map types and how to send them to the fragment function using different indices.

➤ Open Common.h in the Shaders folder, and add a new enumeration to keep track of these texture buffer index numbers:

```
typedef enum {
  BaseColor = 0
} TextureIndices;
```

➤ Open **VertexDescriptor.swift**, and add this code to the end of the file:

```
extension TextureIndices {
  var index: Int {
    return Int(self.rawValue)
  }
}
```

This code allows you to use BaseColor.index instead of Int(BaseColor.rawValue)). A small touch, but it makes your code easier to read.

➤ Open Rendering.swift. This is where you render the model.

In render(encoder:uniforms:params:) where you process the submeshes, add the following code below the comment // set the fragment texture here:

```
encoder.setFragmentTexture(
  submesh.textures.baseColor,
  index: BaseColor.index)
```

You’re now passing the texture to the fragment function in texture buffer 0.

Note: Buffers, textures and sampler states are held in argument tables. As you’ve seen, you access these things by index numbers. On iOS, you can hold at least 31 buffers and textures, and 16 sampler states in the argument table; the number of textures on macOS increases to 128. You can find out feature availability for your device in Apple’s Metal Feature Set Tables (https:// apple.co/2UpCT8r).

<a id="page-189"></a>

## **3. Updating the Fragment Function**

➤ Open Fragment.metal, and add the following new argument to fragment\_main, immediately after VertexOut in [[stage\_in]],:

`texture2d<float> baseColorTexture [[texture(BaseColor)]]`

You’re now able to access the texture on the GPU.

➤ Replace all the code in `fragment_main` with:

`constexpr sampler textureSampler;`

When you read or sample the texture, you may not land precisely on a particular pixel. In texture space, the units that you sample are known as texels, and you can decide how each texel is processed using a sampler. You’ll learn more about samplers shortly.

➤ Next, add this:

```
float3 baseColor = baseColorTexture.sample(
  textureSampler,
  in.uv).rgb;
return float4(baseColor, 1);
```

Here, you sample the texture using the interpolated UV coordinates sent from the vertex function, and you retrieve the RGB values. In Metal Shading Language, you can use rgb to address the float elements as an equivalent of xyz. You then return the texture color from the fragment function.

➤ Build and run the app to see your textured house.

![Figure](Metal_by_Tutorials_v500mpdf/6dc3cc49133b9ed2775aa2cc.png)

_The textured house_

<a id="page-190"></a>

## **The Ground Plane**

It’s time to add some ground to your scene. Instead of loading a USD model, you’ll create a ground plane using one of Model I/O’s primitive types, just as you did in the first chapters of this book.

➤ Open **Primitive.swift** and make sure that you understand the code.

Model I/O creates the MDLMesh for a plane or a sphere, and initializes the Mesh and Submesh. Notice that you can assign your own vertex descriptor after loading the MDLMesh, and Model I/O will automatically rearrange the vertex attribute order in the mesh buffers.

➤ Open Renderer.swift, and add a new property to Renderer to create a ground model:

```
lazy var ground: Model = {
  Model(name: "ground", primitiveType: .plane)
}()
```

➤ In draw(in:) after rendering the house and before renderEncoder.endEncoding(), add:

```
ground.scale = 40
ground.rotation.z = Float(90).degreesToRadians
ground.rotation.y = sin(timer)
ground.render(
  encoder: renderEncoder,
  uniforms: uniforms,
  params: params)
```

This code scales the ground plane up. The plane in its original position is vertical, so you rotate it on the z axis by 90 degrees, and rotate it on the y axis to match the rotation of the house. You then render the ground plane.

<a id="page-191"></a>

➤ Build and run the app to see your ground plane.

![Figure](Metal_by_Tutorials_v500mpdf/311cf8d99b77a7677b5ade52.png)

_The ground plane_

Currently the ground has no texture or color, but you’ll soon fix that by loading a texture from the asset catalog.

## **The Asset Catalog**

When you write your full game, you’re likely to have many textures for the different models. If you use USD format models, the textures will generally be included. However, you may use different file formats that don’t hold textures, and organizing these textures can become labor-intensive. Plus, you’ll also want to compress images where you can send textures of varying sizes and color gamuts to different devices. The asset catalog is where you’ll turn.

As its name suggests, the asset catalog can hold all of your assets, whether they be data, images, textures or even colors. You’ve probably used the catalog for app icons and images. Textures differ from images in that the GPU uses them, and thus they have different attributes in the catalog. To create textures, you add a new texture set to the asset catalog.

<a id="page-192"></a>

➤ Create a new file in the Textures folder, using the Asset Catalog template (found in the Resource section), and name it Textures.

➤ With Textures.xcassets open, choose Editor ▸ Add New Asset ▸ AR and Textures ▸ Texture Set (or click the + at the bottom of the panel and choose AR and Textures ▸ Texture Set).

➤ Rename the new texture grass.

➤ Open the resources folder for this chapter, and drag ground.png to the Universal slot in your catalog.

Note: Be careful to drop the images on the texture’s Universal slot. If you drag the images into the asset catalog, they are, by default, images and not textures. You won’t be able to change any texture attributes later.

![Figure](Metal_by_Tutorials_v500mpdf/cbd0435ff18b2d48c1d6494d.png)

_The grass texture_

You’ll need to add another method to the texture controller to load the named texture from the asset catalog.

➤ Open TextureController.swift, and add a new method to TextureController:

```
static func loadTexture(name: String) -> MTLTexture? {
  // 1
  if let texture = textures[name] {
    return texture
  }
  // 2
  let textureLoader = MTKTextureLoader(device: Renderer.device)
  let texture: MTLTexture?
  texture = try? textureLoader.newTexture(
```

<a id="page-193"></a>

```
    name: name,
    scaleFactor: Renderer.scaleFactor,
    bundle: Bundle.main,
    options: nil)
  // 3
  if texture != nil {
    print("loaded texture: \(name)")
    textures[name] = texture
  }
  return texture
}
```

Going through the code:

1. If you have already loaded a texture of this name return the loaded texture.

2. Set up the texture loader as you did for the USD texture loading. Load the texture from the asset catalog, specifying the name. You’ll set up Renderer.scaleFactor in a moment. The scale factor is the mapping of logical points to the physical screen resolution. Most device screens have a scale factor of 2.0, but the iPhone 16 Pro Max has a scale factor of 3.0.

3. If the texture loads correctly, print out a debug statement, and save it in the texture controller.

Now you’ll assign this texture to the ground plane.

➤ Open **Model.swift**, and add this to the end of the file:

```
extension Model {
  func setTexture(name: String, type: TextureIndices) {
    if let texture = TextureController.loadTexture(name: name) {
      switch type {
      case BaseColor:
        meshes[0].submeshes[0].textures.baseColor = texture
      default: break
      }
    }
  }
}
```

This method loads the texture and assigns it to the model’s first submesh.

<a id="page-194"></a>

Note: This is a quick and easy fix for assigning the texture. It will only work on simple models with only one material. If you frequently load your submesh textures from the asset catalog, you should set up a Submesh initializer that points to the correct textures.

The last thing to do is set the texture on the ground plane, and define the renderer’s scale factor.

➤ Open **Renderer.swift**, and replace the declaration of `ground` with:

```
lazy var ground: Model = {
  let ground = Model(name: "ground", primitiveType: .plane)
  ground.setTexture(name: "grass", type: BaseColor)
  return ground
}()
```

Here, after loading the model, you load the grass texture from the asset catalog and assign it to the ground plane.

➤ Add a new property to Renderer:

`static var scaleFactor: CGFloat = 1`

➤ In init(metalView:), add this code after setting metalView.device:

```
#if os(macOS)
  Self.scaleFactor = NSScreen.main?.backingScaleFactor ?? 1
#elseif os(iOS)
  Self.scaleFactor = metalView.traitCollection.displayScale
#endif
```

Here, you set the screen scale factor depending on the operating system.

<a id="page-195"></a>

➤ Build and run the app to see the flourishing green grass:

![Figure](Metal_by_Tutorials_v500mpdf/add5cc52b251603826659e56.png)

_Dark grass texture_

This looks like a problem. The grass is much darker than the original texture, and it’s stretched and pixellated.

## **sRGB Color Space**

The rendered texture looks much darker than the original image because ground.png is an sRGB texture, and your view’s render target is not sRGB.

sRGB is a standard color format that has a long history. It compromises between how the old cathode ray tube monitors worked and what colors the human eye sees. As you can see in the following example of encoded grayscale values from 0 to 1, sRGB colors are not linear. sRGB uses gamma encoding to distribute brightness values to correspond to human vision.

![Figure](Metal_by_Tutorials_v500mpdf/df0f0bc0761977c914bb93ea.png)

Unfortunately, it’s not easy to do the math on colors in a non-linear space. If you multiply a color by 0.5 to darken it, the difference in sRGB will vary along the scale.

<a id="page-196"></a>

The GPU loads sRGB textures and automatically converts them to linear. So when you’re sampling a value of, say 0.2, which in sRGB space is mid-gray, the linear space will read that as dark-gray. The GPU will then convert the result of the fragment function to the view’s pixel format. This is currently set to linear.

To approximately convert the color to sRGB, in the fragment function, you can use the inverse of gamma 2.2:

`sRGBcolor = pow(linearColor, 1.0/2.2);`

If you use this formula on baseColor before returning from the fragment function, your grass texture will look about the same as the original sRGB texture, but the house texture will be washed out, because it is a non-sRGB texture.

At the time of writing, the house texture highlights a problem with the Model I/O framework’s texture loading from USD files. Color textures are supposed to be sRGB, as they are generally artist-created in sRGB color space. However, Model I/O loads all textures from USD files in linear color space.

Because changing the gamma in the fragment function doesn’t work for all textures, you have two choices:

1. Ensure all textures are non-sRGB and render into a non-sRGB render target.

2. Ensure all textures are sRGB and render into an sRGB render target.

The second option is preferable, as most displays use the sRGB color space natively.

You’ll first change the view’s render target to use the sRGB color space. Then, to overcome Model I/O‘s USD texture loading problem, you’ll convert to sRGB when you load the submesh base color texture.

➤ Open Renderer.swift and, in init(metalView:), locate metalView.device = device. After this code, add:

`metalView.colorPixelFormat = .bgra8Unorm_srgb`

Here, you change the view’s pixel format from the default bgra8Unorm to the format that converts between sRGB and linear space.

<a id="page-197"></a>

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/4c08b5d7078063ad45a72825.png)

_View with sRGB color pixel format_

The grass color is much better now, but your non-sRGB house texture is washed out.

## **Capture GPU Workload**

Before continuing with the texture conversion change, you’ll take a closer look at how the GPU sees your textures, and also examine all the other Metal buffers currently residing there. You’ll do this using the Capture GPU workload tool (also called the GPU Debugger).

➤ Run your app, and at the bottom of the Xcode window (or above the debug console if you have it open), click the M Metal icon, change the number of frames to count to 1, and click Capture in the pop-up window:

![Figure](Metal_by_Tutorials_v500mpdf/aaafa6981cf0e5b7929d0c25.png)

_GPU capture_

<a id="page-198"></a>

This button captures the current GPU frame. On the left in the Debug navigator, you’ll see the GPU trace:

![Figure](Metal_by_Tutorials_v500mpdf/c8a1985e740e3e0e8fbb0846.png)

_A GPU trace_

Note: To open or close all items in a hierarchy, you can Option-click the arrow.

You can see all the commands that you’ve given to the render command encoder, such as setFragmentBytes and setRenderPipelineState. Later, when you have several command encoders, you’ll see each one of them listed, and you can select them to see what actions or textures they have produced from their encoding.

<a id="page-199"></a>

➤ Select the first drawIndexedPrimitives at step 11. The Vertex and Fragment resources show.

![Figure](Metal_by_Tutorials_v500mpdf/ac3e3fe594fb615186d3ca9b.png)

_Resources on the GPU_

➤ Double-click each resource to see what’s in the buffer:

The render pipeline state and its functions:

• vertex\_main: The vertex function. When you have multiple vertex functions, this is useful to make sure that you set the correct pipeline state.

• fragment\_main: The fragment function.

The vertex resources:

• indices: The submesh indices.

• Buffer 0: The vertex position and normal data, matching the attributes of your VertexIn struct and the vertex descriptor.

• Buffer 1: The UV texture coordinate data.

• Vertex Bytes: The uniform matrices.

• Vertex Attributes: The incoming data from VertexIn, and the VertexOut return data from the vertex function. This resource in particular is useful to see the results of your vertex function’s calculations.

• Geometry: A visual representation of the vertices when the vertex function is complete.

<a id="page-200"></a>

Going through the fragment resources:

• Texture 0: The house texture in texture slot 0.

• Fragment Bytes: The width and height screen parameters in params.

The frame attachments:

• Texture Color 0: The result of the encoding in color attachment 0. In this case, this is the view’s current drawable. Later, you’ll use multiple color attachments.

• MTKView Depth: The depth buffer. Black is closer. White is farther away.

➤ Control-click **Texture 0** and choose **Get Info** from the popup menu.

![Figure](Metal_by_Tutorials_v500mpdf/c22228e3f707100174f53086.png)

_Texture info_

The pixel format is `RGBA8Unorm`, not sRGB.

➤ In the Debug navigator, click the second drawIndexedPrimitives command at step 17. Again, control-click the grass texture and choose Get Info from the popup menu.

The pixel format this time is RGBA8Unorm\_sRGB. You can confirm that the render target is also sRGB by control-clicking Texture Color 0.

If you’re ever uncertain as to what is happening in your app, capturing the GPU frame might give you the heads-up because you can examine every render encoder command and every buffer. It’s a good idea to use this strategy throughout this book to examine what’s happening on the GPU.

<a id="page-201"></a>

Now to return to your problem with the mismatched textures.

➤ Open Submesh.swift and locate MDLMaterial.texture(type:) in the MDLMaterial extension.

➤ Replace:

```
return TextureController.loadTexture(
  texture: mdlTexture,
  name: property.textureName)
```

➤ With this code:

```
var texture = TextureController.loadTexture(
  texture: mdlTexture,
  name: property.textureName)
if semantic == .baseColor,
  texture?.pixelFormat == .rgba8Unorm {
  texture =
texture?.makeTextureView(pixelFormat: .rgba8Unorm_srgb)
  TextureController.textures[property.textureName] = texture
}
return texture
```

Your app currently only loads MDLTextures for USD files. If this changes in the future, or Apple decide to load USD base color textures with a different pixel format, you may have to revise this fix.

MTLTexture.makeTextureView(pixelFormat:) reinterprets the texture data. You need to be sure that the pixel formats are compatible. Here, the loaded pixel format is linear, so you create a texture view that is sRGB.

➤ Open TextureController.swift and locate let textureLoaderOptions: in loadTexture(texture:name:). Add a new option:

.textureUsage: MTLTextureUsage.pixelFormatView.rawValue   | MTLTextureUsage.shaderRead.rawValue

This is necessary for iOS Simulator because Simulator has a stricter texture usage validation. You set up the texture so that you can change the pixel format view and read it in shader functions.

<a id="page-202"></a>

➤ Build and run the app, and, with the render target set to sRGB and both textures sRGB, the render is now correct. You can confirm the formats by capturing the GPU workload again.

![Figure](Metal_by_Tutorials_v500mpdf/3fc25a3eb310a447a721925d.png)

_Color space correction_

Now you can deal with the other problems in your render, starting with the pixellated grass.

## **Samplers**

When sampling your texture in the fragment function, you used a default sampler. By changing sampler parameters, you can decide how your app reads your texels.

The ground texture stretches to fit the ground plane, and each pixel in the texture may be used by several rendered fragments, giving it a pixellated look. By changing one of the sampler parameters, you can tell Metal how to process the texel where it’s smaller than the assigned fragments.

➤ Open Fragment.metal. In fragment\_main, change the textureSampler definition to:

`constexpr sampler textureSampler(filter::linear);`

This code instructs the sampler to smooth the texture.

<a id="page-203"></a>

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/96b24b376224b35a4876b06b.png)

_A smoothed texture_

The ground texture — although still stretched — is now smooth. There will be times, such as when you make a retro game of Frogger, that you’ll want to keep the pixelation. In that case, use nearest filtering.

![Figure](Metal_by_Tutorials_v500mpdf/bc5d59589e0c1819f1a3cb60.png)

_Filtering_

In this particular case, however, you want to tile the texture. That’s easy with sampling.

➤ Change the sampler definition and the `baseColor` assignment to:

```
constexpr sampler textureSampler(
  filter::linear,
  address::repeat);
float3 baseColor = baseColorTexture.sample(
  textureSampler,
  in.uv * 16).rgb;
```

<a id="page-204"></a>

This code multiplies the UV coordinates by 16 and accesses the texture outside of the allowable limits of 0 to 1. address::repeat changes the sampler’s addressing mode, so it’ll repeat the texture 16 times across the plane.

The following image illustrates the other address sampling options shown with a tiling value of 3. You can use s\_address or t\_address to change only the width or height coordinates, respectively.

![Figure](Metal_by_Tutorials_v500mpdf/ef318de19a55ee24bebc1422.png)

_The sampler address mode_

➤ Build and run your app.

![Figure](Metal_by_Tutorials_v500mpdf/413b48daa92224d2aa2d421d.png)

_Texture tiling_

The ground looks great! The house… not so much. The shader has tiled the house texture as well. To overcome this problem, you’ll create a tiling property on the model and send it to the fragment function with params.

➤ In Common.h, add this to Params:

`uint32_t tiling;`

<a id="page-205"></a>

➤ In Model.swift, create a new property in Model:

`var tiling: UInt32 = 1`

➤ Open Rendering.swift, and in render(encoder:uniforms:params:), just after var params = fragment, add this:

`params.tiling = tiling`

➤ In **Renderer.swift**, replace the declaration of `ground` with:

```
lazy var ground: Model = {
  let ground = Model(name: "ground", primitiveType: .plane)
  ground.setTexture(name: "grass", type: BaseColor)
  ground.tiling = 16
  return ground
}()
```

You’re now sending the model’s tiling factor to the fragment function.

➤ Open Fragment.metal. In fragment\_main, replace the declaration of baseColor with:

```
float3 baseColor = baseColorTexture.sample(
  textureSampler,
  in.uv * params.tiling).rgb;
```

➤ Build and run the app, and you’ll see that both the ground and house now tile correctly.

![Figure](Metal_by_Tutorials_v500mpdf/c78f2ac0f0b46dbf54424d3e.png)

_Corrected tiling_

<a id="page-206"></a>

Note: Creating a sampler in the shader is not the only option. You can create an MTLSamplerState, hold it with the model and send the sampler state to the fragment function with the [[sampler(n)]] attribute.

As the scene rotates, you’ll notice some distracting noise. You’ve seen what happens on the grass when you oversample a texture. But, when you undersample a texture, you can get a rendering artifact known as moiré, which is occurring on the roof of the house.

![Figure](Metal_by_Tutorials_v500mpdf/b569439936e79fec8a4a6d2e.png)

_A moiré example_

In addition, the noise at the horizon almost looks as if the grass is sparkling. You can solve these artifact issues by sampling correctly using resized textures called mipmaps.

## **Mipmaps**

Check out the relative sizes of the roof texture and how it appears on the screen.

![Figure](Metal_by_Tutorials_v500mpdf/592153c8ff7b35f200628b35.png)

_Size of texture compared to on-screen viewing_

<a id="page-207"></a>

The pattern occurs because you’re sampling more texels than you have pixels. The ideal would be to have the same number of texels to pixels, meaning that you’d require smaller and smaller textures the further away an object is. The solution is to use mipmaps. Mipmaps let the GPU compare the fragment on its depth texture and sample the texture at a suitable size.

MIP stands for multum in parvo — a Latin phrase meaning “much in small”.

Mipmaps are texture maps resized down by a power of 2 for each level, all the way down to 1 pixel in size. If you have a texture of 64 pixels by 64 pixels, then a complete mipmap set would consist of:

Level 0: 64 x 64, 1: 32 x 32, 2: 16 x 16, 3: 8 x 8, 4: 4 x 4, 5: 2 x 2, 6: 1 x 1.

![Figure](Metal_by_Tutorials_v500mpdf/7d62aceaf91655e4f01b5e80.png)

_Mipmaps_

In the following image, the top checkered texture has no mipmaps. But in the bottom image, every fragment is sampled from the appropriate MIP level.

![Figure](Metal_by_Tutorials_v500mpdf/6add4b3dc293580145c0e2aa.png)

_Mipmap comparison_

<a id="page-208"></a>

As the checkers recede, there’s much less noise, and the image is cleaner. At the horizon, you can see the solid color smaller gray mipmaps.

You can easily and automatically generate these mipmaps when first loading the texture.

➤ To set up the USD textures, open TextureController.swift. In loadTexture(texture:name:), change the texture loading options to:

```
let textureLoaderOptions: [MTKTextureLoader.Option: Any] = [
  .origin: MTKTextureLoader.Origin.bottomLeft,
  .textureUsage: MTLTextureUsage.pixelFormatView.rawValue
    | MTLTextureUsage.shaderRead.rawValue,
  .generateMipmaps: true
]
```

This code will create mipmaps all the way down to the smallest pixel.

There’s one more thing to change: the texture sampler in the fragment shader.

➤ Open Fragment.metal, and add the following code to the construction of textureSampler:

`mip_filter::linear`

The default for mip\_filter is none. However, if you provide either .linear or .nearest, then the GPU will sample the correct mipmap.

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/a597a8ff4cf04cc00b347937.png)

_Mipmaps added_

<a id="page-209"></a>

The noise from both the building and the ground is gone.

Using the Capture GPU workload tool, you can inspect the mipmaps. Choose the draw call, and double-click a texture.

![Figure](Metal_by_Tutorials_v500mpdf/29ad1636fb2c95a4aac67cf5.png)

_House mipmaps_

You can see all the mipmap textures of varying sizes. The GPU will automatically load the appropriate mipmap.

<a id="page-210"></a>

## **Asset Catalog Attributes**

Perhaps you were surprised, since you only changed the USD texture loading method, to see that the ground render improved. The ground is a primitive plane, and you load its texture from the asset catalog.

➤ In the Textures folder, open Textures.xcassets, and with the Attributes inspector open, click on the grass texture to see all of the texture options.

![Figure](Metal_by_Tutorials_v500mpdf/dacf0eb7c17626cd08945493.png)

_Texture attributes in the asset catalog_

Here, you can see that by default, all mipmaps are created automatically. If you change Mipmap Levels to Fixed, you can choose how many levels to make. If you don’t like the automatic mipmaps, you can replace them with your own custom mipmaps by dragging them to the correct slot.

![Figure](Metal_by_Tutorials_v500mpdf/39946580a2691c019c05467f.png)

_Mipmap slots_

<a id="page-211"></a>

## **The Right Texture for the Right Job**

Using asset catalogs gives you complete control over how to deliver your textures. Currently, you only have one color texture for the grass. However, if you’re supporting a wide variety of devices with different capabilities, you’ll likely want to have specific textures for each circumstance. On devices with less RAM, you’d want smaller graphics.

For example, here is a list of textures you can assign by checking the different options in the Attributes inspector, for the Apple Watch, and sRGB and P3 displays.

![Figure](Metal_by_Tutorials_v500mpdf/07b97f27bcf5669c276d0435.png)

_Custom textures in the asset catalog_

## **Anisotropy**

Your rendered ground is looking a bit muddy and blurred in the background. This is due to anisotropy. Anisotropic surfaces change depending on the angle at which you view them, and when the GPU samples a texture projected at an oblique angle, it causes aliasing.

➤ In Fragment.metal, add this to the construction of textureSampler:

`max_anisotropy(8)`

<a id="page-212"></a>

Metal will now take eight samples from the texel to construct the fragment. You can specify up to 16 samples to improve quality. Use as few as you can to obtain the quality you need because the sampling can slow down rendering.

Note: As mentioned before, you can hold an MTLSamplerState on Model. If you increase anisotropy sampling, you may not want it on all models, and this might be a good reason for creating the sampler state outside the fragment shader.

➤ Build and run, and your render should be artifact-free.

![Figure](Metal_by_Tutorials_v500mpdf/cec916bbddd95aa4abb02b0a.png)

_Anisotropy_

You may notice that the edge of the ground still has “jaggies”. You’ll take a look at Multisample Antialiasing (MSAA) in Chapter 20, “Fragment Processing”.

<a id="page-213"></a>

## **Challenge**

In the resources folder for this chapter, you’ll find two textures:

• barn-color.png

• barn-ground.png

Add these two textures to the asset catalog and replace the current textures for the house and ground with these. Aside from adding the textures, all you have to change is the initialization of the house model in Renderer as described in this chapter. If you have any difficulties, check out the challenge folder for this chapter.

![Figure](Metal_by_Tutorials_v500mpdf/9f85c057cbd96b0a93a9dc22.png)

_Barn textures_

<a id="page-214"></a>

## **Key Points**

• UVs, also known as texture coordinates, match vertices to the location in a texture.

• During the modeling process, you flatten the model by marking seams. You can then paint on a texture that matches the flattened model map.

• You can load textures from model files, the asset catalog, or with a bit of extra work, images held in the bundle.

• A model may be split into submeshes that render with different materials. Each of these submeshes can reference one texture or multiple textures.

• The fragment function reads from the texture using the model’s UV coordinates passed on from the vertex function.

• The sRGB color space is the default color gamut. Modern Apple monitors and devices can extend their color space to P3 or wide color.

• Capture GPU workload is a useful debugging tool. Use it regularly to inspect what’s happening on the GPU.

• Mipmaps are resized textures that match the fragment sampling. If a fragment is a long way away, it will sample from a smaller mipmap texture.

• Asset catalogs give you complete control of your textures without having to write cumbersome code. Customization for different devices is easy using the asset catalog.

• Topics such as color and compression are huge. In the resources folder for this chapter, in references.markdown, you’ll find some recommended articles to read further.

<a id="page-215"></a>

# 9

# Chapter 9: Navigating a 3D Scene

A scene can consist of one or more cameras, lights and models. Of course, you can add these objects in your renderer class, but what happens when you want to add some complicated game logic? Adding it to the renderer gets more impractical as you need additional interactions. Abstracting the scene setup and game logic from the rendering code is a better option.

Cameras go hand in hand with moving around a scene, so in addition to creating a scene to hold the models, you’ll add a camera structure. Ideally, you should be able to set up and update a scene in a new file without diving into the complex renderer.

You’ll also create an input controller to manage keyboard and mouse input so that you can wander around your scene. Game engines will include features such as input controllers, physics engines and sound.

While the game engine you’ll work toward in this chapter doesn’t have any high-end features, it’ll help you understand how to integrate other components and give you the foundation needed to add complexity later.

<a id="page-216"></a>

## **The Starter Project**

Aside from some helpful comments in Renderer, the starter project for this chapter is the same as the challenge project for the previous chapter.

## **Scenes**

A scene holds models, cameras and lighting. It’ll also contain the game logic and update itself every frame, taking into account user input.

➤ Open the starter project. Under the Navigation folder, create a new folder named Game. Inside this folder, create a new Swift file named GameScene.swift and replace the code with:

```
import MetalKit

struct GameScene {
}
```

If you created a structure named Scene rather than GameScene, there would be a conflict with the SwiftUI Scene you use in NavigationApp.swift. If you really want to use Scene, you can add the explicit namespace to Scene in NavigationApp.swift using SwiftUI.Scene. But it’s best to remember that Scenes belong to SwiftUI.

➤ Add this code to GameScene:

```
  lazy var house: Model = {
    let house = Model(name: "lowpoly-house.usdz")
    house.setTexture(name: "barn", type: BaseColor)
    return house
  }()
  lazy var ground: Model = {
    let ground = Model(name: "ground", primitiveType: .plane)
    ground.setTexture(name: "grass", type: BaseColor)
    ground.tiling = 16
    ground.transform.scale = 40
    ground.transform.rotation.z = Float(90).degreesToRadians
    return ground
  }()
  lazy var models: [Model] = [ground, house]
```

<a id="page-217"></a>

You’ll create and set up your models in GameScene, rather than Renderer.

➤ Open Renderer.swift, and remove the instantiation of house and ground.

➤ Add a new property:

`lazy var scene = GameScene()`

You still have some compile errors in draw(in:) because you removed house and ground. You’ll fix those shortly.

At the moment, you rotate the models just before drawing them, but it’s a good idea to separate update and render. GameScene will update the models, and Renderer will render them.

➤ Open GameScene.swift and add a new update method to GameScene:

```
mutating func update(deltaTime: Float) {
  ground.rotation.y = sin(deltaTime)
  house.rotation.y = sin(deltaTime)
}
```

Here, you perform the rotation, which is currently in Renderer.

You’ll calculate deltaTime, which is the amount of time that has passed since the previous frame soon. You’ll pass this from Renderer to GameScene.

➤ In Renderer.swift, in draw(in:), replace everything between // update and render to // end update and render with:

```
 scene.update(deltaTime: timer)
 for model in scene.models {
   model.render(
     encoder: renderEncoder,
     uniforms: uniforms,
     params: params)
 }
```

<a id="page-218"></a>

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/d4785a75e660727674250802.png)

_The initial scene_

Here, you reduce the complexity of draw(in:), separate the update from the render and set up the scene to handle its own updates. You can also more easily add and update models in GameScene.

## **Cameras**

Instead of creating view and projection matrices in the renderer, you can abstract the construction and calculation away from the rendering code to a Camera structure. Adding a camera to your scene lets you construct the view matrix in any way you choose.

Currently, you rotate the scene by rotating both house and ground in the y axis. While it looks to the viewer as if a camera is rotating around the scene, in fact, the view matrix doesn’t change. Now you’ll explore how to move a camera around the scene with keyboard and mouse input.

Setting up a camera is simply a way of calculating a view matrix. Miscalculating the view matrix is a frequent pain point where your carefully rendered objects result in a blank screen. So, it’s worth spending time working out common camera setups.

<a id="page-219"></a>

➤ In the Game folder, create a new Swift file named Camera.swift, and replace the existing code with:

```
import CoreGraphics

protocol Camera: Transformable {
  var projectionMatrix: float4x4 { get }
  var viewMatrix: float4x4 { get }
  mutating func update(size: CGSize)
  mutating func update(deltaTime: Float)
}
```

Cameras have a position and rotation, so they should conform to Transformable. All cameras have a projection and view matrix as well as methods to perform when the window size changes and when each frame updates.

➤ Create a custom camera:

```
struct FPCamera: Camera {
  var transform = Transform()
}
```

You created a first-person camera. Eventually, this camera will move forward when you press the W key. You’ll get a compile error until you’ve completed the following code.

➤ Add this code to FPCamera:

```
var aspect: Float = 1.0
var fov = Float(70).degreesToRadians
var near: Float = 0.1
var far: Float = 100
var projectionMatrix: float4x4 {
  float4x4(
    projectionFov: fov,
    near: near,
    far: far,
    aspect: aspect)
}
```

Currently, you set up the projection matrix in Renderer‘s mtkView(\_:drawableSizeWillChange:). You’ll remove that code in Renderer shortly.

<a id="page-220"></a>

➤ Add a new method to update the camera’s aspect ratio:

```
mutating func update(size: CGSize) {
  aspect = Float(size.width / size.height)
}
```

➤ Add the camera’s view matrix calculation:

```
var viewMatrix: float4x4 {
  (float4x4(rotation: rotation) *
  float4x4(translation: position)).inverse
}
```

Each camera calculates its own projection and view matrix. You’ll change this view matrix in a moment. But first, you’ll run the app to see what this matrix does.

➤ Add the update method:

```
mutating func update(deltaTime: Float) {
}
```

This method repositions the camera every frame.

You’ve now set up all the properties and methods required to conform to Camera.

➤ Open **GameScene.swift**, and add a new camera property:

`var camera = FPCamera()`

➤ Then, add an initializer to GameScene:

```
init() {
  camera.position = [0, 1.4, -4.0]
}
```

➤ Create a new method:

```
mutating func update(size: CGSize) {
  camera.update(size: size)
}
```

This code will update the camera when the screen size changes.

<a id="page-221"></a>

➤ Open Renderer.swift and replace the entire contents of mtkView(\_:drawableSizeWillChange:) with:

`scene.update(size: size)`

When the screen size changes, the scene update calls the camera update, which in turn updates the aspect ratio needed for the projection matrix.

➤ In `draw(in:)`, after `scene.update(deltaTime: timer)`, add:

```
uniforms.viewMatrix = scene.camera.viewMatrix
uniforms.projectionMatrix = scene.camera.projectionMatrix
```

Here, you set up the uniforms the vertex shader requires.

➤ Next, remove the previous viewMatrix assignment at the top of draw(in:):

```
uniforms.viewMatrix =
  float4x4(translation: [0, 1.4, -4.0]).inverse
```

Now, instead of rotating the ground and the house, you can easily rotate the camera.

➤ Open GameScene.swift. In update(deltaTime:), replace:

```
ground.rotation.y = sin(deltaTime)
house.rotation.y = sin(deltaTime)
```

With:

`camera.rotation.y = sin(deltaTime)`

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/8e66d38d8165da1680e99e40.png)

_The camera rotating_

<a id="page-222"></a>

The scene looks the same, but instead of rotating the house and ground, the camera now rotates around the world origin. When you update the view matrix, the vertex shader code updates the final transformation of all the models in the scene.

However, you don’t want the camera to rotate around the world origin in a first-person camera: You want it to rotate around its own origin.

➤ Open **Camera.swift**, and change `viewMatrix` in `FPCamera` to:

```
var viewMatrix: float4x4 {
  (float4x4(translation: position) *
  float4x4(rotation: rotation)).inverse
}
```

Here, you reverse the order of matrix multiplication so that the camera rotates around its own origin.

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/e9b2ad940c0db30cb026dfac.png)

_The camera rotating around its center_

The camera now rotates in place. Next, you’ll set up keys to move around the scene.

<a id="page-223"></a>

## **Input**

There are various forms of input, such as game controllers, keyboards, mice and trackpads. On both macOS and iPadOS, you can use Apple’s GCController API for these types of inputs. This API helps you set your code up for:

• Events or Interrupts: Takes action when the user presses the key. You can set delegate methods or closures of code to run when an event occurs.

• Polling: Processes all pressed keys on every frame.

In this app, you’ll use polling to move your cameras and players. It’s a personal choice, and neither method is better than the other.

The input code you’ll build works on macOS and iPadOS if you connect a keyboard and mouse to your iPad. If you want input on your iPhone or iPad without extra controllers, use GCVirtualController, which lets you configure on-screen controls that emulate a game controller. You can download Apple’s Supporting Game Controllers sample code (https://apple.co/3qfeL60) that demonstrates this.

➤ In the Game folder, create a new Swift file named InputController.swift, and replace the code with:

```
import GameController

class InputController {
  static let shared = InputController()
}
```

This code creates a singleton input controller that you can access throughout your app.

➤ Add a new property to InputController:

`var keysPressed: Set<GCKeyCode> = []`

In this set, `InputController` keeps track of all keys currently pressed.

To track the keyboard, you need to set up an observer.

➤ Add this initializer:

```
private init() {
  let center = NotificationCenter.default
  center.addObserver(
    forName: .GCKeyboardDidConnect,
```

<a id="page-224"></a>

```
    object: nil,
    queue: nil) { notification in
      let keyboard = notification.object as? GCKeyboard
        keyboard?.keyboardInput?.keyChangedHandler
          = { _, _, keyCode, pressed in
        if pressed {
          self.keysPressed.insert(keyCode)
        } else {
          self.keysPressed.remove(keyCode)
        }
      }
  }
}
```

Here, you add an observer to set the keyChangedHandler when the keyboard first connects to the app. When the player presses or lifts a key, the keyChangedHandler code runs and either adds or removes the key from the set.

Now test to see if it works.

➤ Open **GameScene.swift**, and import the required framework at the top of the file:

`import GameController`

➤ Add this to the end of update(deltaTime:):

```
if InputController.shared.keysPressed.contains(.keyH) {
  print("H key pressed")
}
```

➤ Build and run the app. Then press different keys.

Press the **H** key in the console and you’ll see your print log.

![Figure](Metal_by_Tutorials_v500mpdf/d3a1a7c10eba26357b6146c9.png)

Notice the annoying warning ‘beep’ from macOS when you press the keys.

➤ Open InputController.swift, and add this to the end of init():

```
#if os(macOS)
  NSEvent.addLocalMonitorForEvents(
    matching: [.keyUp, .keyDown]) { _ in nil }
#endif
```

<a id="page-225"></a>

Here, on macOS only, you interrupt the view’s responder chain by handling any key presses and telling the system that it doesn’t need to take action when a key is pressed. You don’t need to do this for iPadOS, as the iPad doesn’t make the keyboard noise.

Note: You could add keys to keysPressed in this code instead of using the observer. However, that wouldn’t work on iPadOS, and GCKeyCode is easier to read than the raw key values that NSEvent gives you.

➤ Build and rerun the app. Test pressing keys.

The noise is gone. If you have a Bluetooth keyboard and an iPad device, connect the keyboard to the iPad and test that it also works on iPadOS.

➤ Open **GameScene.swift**, and remove the key testing code.

You can now capture any pressed key. Soon, you’ll set up standard movement keys to move the camera.

## **Delta Time**

First, you’ll set up the left and right arrows on the keyboard to control the camera’s rotation.

When considering movement, think about how much time has passed since the last movement occurred. In an ideal world, at 60 frames per second, a frame should take 0.01667 milliseconds to execute. However, some displays can produce 120 frames per second or even a variable refresh rate.

If you get a choppy frame rate, you can smooth out the movement by calculating delta time, which is the amount of time since the previous execution of the code.

➤ Open **Renderer.swift**, and replace `var timer: Float 0` with:

`var lastTime: Double = CFAbsoluteTimeGetCurrent()`

lastTime holds the time from the previous frame. You initialize it with the current time.

<a id="page-226"></a>

➤ In `draw(in:)`, remove:

`timer += 0.005`

➤ Replace `scene.update(deltaTime: timer)` with:

```
let currentTime = CFAbsoluteTimeGetCurrent()
let deltaTime = Float(currentTime - lastTime)
lastTime = currentTime
scene.update(deltaTime: deltaTime)
```

Here, you get the current time and calculate the difference from the last time.

## **Camera Rotation**

➤ Open GameScene.swift. In update(deltaTime:), replace:

`camera.rotation.y = sin(deltaTime)`

With:

`camera.update(deltaTime: deltaTime)`

➤ In the **Game** folder, create a new Swift file named **Movement.swift**, and add:

```
import GameController

enum Settings {
  static var rotationSpeed: Float { 2.0 }
  static var translationSpeed: Float { 3.0 }
  static var mouseScrollSensitivity: Float { 0.1 }
  static var mousePanSensitivity: Float { 0.008 }
}
```

You can tweak these settings to make your camera and mouse movement smooth. Eventually, you might choose to replace Settings with a user interface that sets the values.

• rotationSpeed: How many radians the camera should rotate in one second. You’ll calculate the amount the camera should rotate in delta time.

• translationSpeed: The distance per second that your camera should travel.

• mouseScrollSensitivity and mousePanSensitivity: Settings to adjust mouse tracking and scrolling.

<a id="page-227"></a>

➤ Add a new protocol:

```
protocol Movement where Self: Transformable {
}
```

Your game might move a player object instead of a camera, so make the movement code as flexible as possible. Now you can give any Transformable object Movement.

➤ Create an extension with a default method:

```
extension Movement {
  func updateInput(deltaTime: Float) -> Transform {
    var transform = Transform()
    let rotationAmount = deltaTime * Settings.rotationSpeed
    let input = InputController.shared
    if input.keysPressed.contains(.leftArrow) {
      transform.rotation.y -= rotationAmount
    }
    if input.keysPressed.contains(.rightArrow) {
      transform.rotation.y += rotationAmount
    }
    return transform
  }
}
```

You already told InputController to add and remove key presses to a Set called keysPressed. Here, you find out if keysPressed contains the arrow keys. If it does, you change the transform rotation value.

➤ Open Camera.swift and add the protocol conformance to FPCamera:

`extension FPCamera: Movement { }`

➤ Still in Camera.swift, add this code to update(deltaTime:):

```
let transform = updateInput(deltaTime: deltaTime)
rotation += transform.rotation
```

You update the camera’s rotation with the transform calculated in Movement.

<a id="page-228"></a>

➤ Build and run the app. Now, use the arrow keys to rotate the camera.

![Figure](Metal_by_Tutorials_v500mpdf/0aa5ad56d4e91de0244e68d6.png)

_Using arrow keys to rotate the camera_

## **Camera Movement**

You can implement forward and backward movement the same way using standard WASD keys:

• W: Move forward

• A: Strafe left

• S: Move backward

• D: Strafe right

Here’s what to expect when you move the camera through the scene:

• You’ll move along the x and z axes.

• Your camera will have a direction vector. When you press the W key, you’ll move along the z axis in a positive direction.

• If you press the W and D keys simultaneously, you’ll move diagonally.

• When you press the left and right arrow keys, you’ll rotate in the corresponding direction, which changes the camera’s forward direction vector.

<a id="page-229"></a>

➤ Open Movement.swift, and add a computed property to Movement’s extension:

```
var forwardVector: float3 {
  normalize([sin(rotation.y), 0, cos(rotation.y)])
}
```

This is the forward vector based on the current rotation.

The following image shows an example of forward vectors when rotation.y is 0º and 45º:

![Figure](Metal_by_Tutorials_v500mpdf/e83c811e4193b23a0b360662.png)

_Forward vectors_

➤ Add a computed property to handle strafing from side to side:

```
var rightVector: float3 {
  [forwardVector.z, forwardVector.y, -forwardVector.x]
}
```

This vector points 90º to the right of the forward vector.

➤ Still in `Movement`, at the end of `updateInput(deltaTime:)`, before `return`, add:

```
var direction: float3 = .zero
if input.keysPressed.contains(.keyW) {
  direction.z += 1
}
if input.keysPressed.contains(.keyS) {
  direction.z -= 1
}
if input.keysPressed.contains(.keyA) {
  direction.x -= 1
```

<a id="page-230"></a>

```
}
if input.keysPressed.contains(.keyD) {
  direction.x += 1
}
```

This code processes each depressed key and creates a final desired direction vector. For instance, if the game player presses W and A, she wants to go diagonally forward and left. The final direction vector is [-1, 0, 1].

➤ After the previous code, add:

```
let translationAmount = deltaTime * Settings.translationSpeed
if direction != .zero {
  direction = normalize(direction)
  transform.position += (direction.z * forwardVector
    + direction.x * rightVector) * translationAmount
}
```

Here, you calculate the transform’s position from its current forward and right vectors and the desired direction.

➤ Open Camera.swift, and add this code to the end of update(deltaTime:):

`position += transform.position`

➤ Build and run the app. Now, you can move about your scene using the keyboard controls.

![Figure](Metal_by_Tutorials_v500mpdf/37f2c7e5f7dd54cd631307d6.png)

_Moving around the scene using the keyboard_

<a id="page-231"></a>

## **Mouse and Trackpad Input**

Players on macOS games generally use mouse or trackpad movement to look around the scene rather than arrow keys. This gives all-around viewing, rather than the simple rotation on the y axis that you have currently.

➤ Open InputController.swift, and add a new structure to InputController that you’ll use in place of CGPoint:

```
struct Point {
  var x: Float
  var y: Float
  static let zero = Point(x: 0, y: 0)
}
```

Make sure that Point goes inside InputController to avoid future name conflicts. Point is the same as CGPoint, except it contains Floats rather than CGFloats.

➤ Add these properties to `InputController` to record mouse movement:

```
var leftMouseDown = false
var mouseDelta = Point.zero
var mouseScroll = Point.zero
```

• leftMouseDown: Tracks when the player does a left-click.

• mouseDelta: The movement since the last tracked movement.

• mouseScroll: Keeps track of how much the player scrolls with the mouse wheel.

➤ At the end of `init()`, add:

```
center.addObserver(
  forName: .GCMouseDidConnect,
  object: nil,
  queue: nil) { notification in
    let mouse = notification.object as? GCMouse
}
```

This code to connect the mouse is similar to how you handled the keyboard connection.

➤ Inside the closure, after setting `mouse`, add:

```
// 1
mouse?.mouseInput?.leftButton.pressedChangedHandler = { _, _,
pressed in
```

<a id="page-232"></a>

```
  self.leftMouseDown = pressed
}
// 2
mouse?.mouseInput?.mouseMovedHandler = { _, deltaX, deltaY in
  self.mouseDelta = Point(x: deltaX, y: deltaY)
}
// 3
mouse?.mouseInput?.scroll.valueChangedHandler = { _, xValue,
yValue in
  self.mouseScroll.x = xValue
  self.mouseScroll.y = yValue
}
```

Here, you:

1. Record when the user holds down the left mouse button.

2. Track mouse movement.

3. Record scroll wheel movement. xValue and yValue are normalized values between -1 and 1. If you use a game controller instead of a mouse, the first parameter is dpad, which tells you which directional pad element changed.

Now you’re ready to use these tracked mouse input values.

Note: For iOS, you should use touch values rather than mouse tracking. The challenge project sample sets up MetalView with gestures that update InputController values.

## **Arcball Camera**

In many apps, the camera rotates about a particular point. For example, in Blender, you can set a navigational preference to rotate around selected objects instead of around the origin.

➤ Open Camera.swift. Copy and paste the FPCamera structure without the extension.

➤ Rename the copied structure:

`struct ArcballCamera: Camera {`

<a id="page-233"></a>

➤ Since you’re not implementing Movement, remove all the code from update(deltaTime:).

Your code will now compile.

➤ Open **GameScene.swift** and change the `camera` initialization to:

`var camera = ArcballCamera()`

You now have a camera with no movement.

## **Orbiting a Point**

The camera needs a track to rotate about a point:

• Target: The point the camera will orbit.

• Distance: The distance between the camera and the target. The player controls this with the mouse wheel.

• Rotation: The camera’s rotation about the point. The player controls this by left-clicking the mouse and dragging.

![Figure](Metal_by_Tutorials_v500mpdf/39e93408539557c83210e5c3.png)

_Orbiting a point_

<a id="page-234"></a>

From these three properties, you can determine the camera’s world position and rotate it to always point at the target position. To do this:

1. First, rotate the distance vector around the y axis.

2. Then, rotate the distance vector around the x axis.

3. Add the target position to the rotated vector to get the new world position of the camera.

4. Rotate the camera to look at the target position.

➤ Open Camera.swift, and add the necessary properties to ArcballCamera to keep track of the camera’s orbit:

```
let minDistance: Float = 0.01 // must be > 0
let maxDistance: Float = 20
var target: float3 = [0, 0, 0]
var distance: Float = 2.5
```

You’ll constrain distance with minDistance and maxDistance.

➤ In `update(deltaTime:)`, add:

```
let input = InputController.shared
let scrollSensitivity = Settings.mouseScrollSensitivity
distance -= (input.mouseScroll.x + input.mouseScroll.y)
  * scrollSensitivity
distance = min(maxDistance, distance)
distance = max(minDistance, distance)
input.mouseScroll = .zero
```

Here, you change `distance` depending on the mouse scroll values.

➤ Continue with this code:

```
if input.leftMouseDown {
  let sensitivity = Settings.mousePanSensitivity
  rotation.x += input.mouseDelta.y * sensitivity
  rotation.y += input.mouseDelta.x * sensitivity
  rotation.x = max(-.pi / 2, min(rotation.x, .pi / 2))
  input.mouseDelta = .zero
}
```

<a id="page-235"></a>

If the player drags with the left mouse button, update the camera’s rotation values.

➤ Add this after the previous code:

```
let rotateMatrix = float4x4(
  rotationYXZ: [-rotation.x, rotation.y, 0])
let distanceVector = float4(0, 0, -distance, 0)
let rotatedVector = rotateMatrix * distanceVector
position = target + rotatedVector.xyz
```

Here, you complete the calculations to rotate the distance vector and add the target position to the new vector. In MathLibrary.swift, float4x4(rotationYXZ:) creates a matrix using rotations in Y / X / Z order.

## **The lookAt Matrix**

A lookAt matrix rotates the camera so it always points at a target. In MathLibrary.swift, you’ll find a float4x4 initialization init(eye:target:up:). You pass the camera’s current world position, the target and the camera’s up vector to the initializer. In this app, the camera’s up vector is always [0, 1, 0].

➤ In `ArcballCamera`, replace `viewMatrix` with:

```
  var viewMatrix: float4x4 {
    float4x4(eye: position, target: target, up: [0, 1, 0])
  }
```

You rotate the camera with the `lookAt` matrix.

➤ Open GameScene.swift, and add this to the end of init():

```
camera.distance = length(camera.position)
camera.target = [0, 1.2, 0]
```

With an arcball camera, you set the target and distance as well as the position.

You’ll need to observe system events for third party mice.

<a id="page-236"></a>

➤ Open ContentView.swift, and add this to body, after border(Color.black, width: 2):

```
.onAppear {
#if os(macOS)
  NSEvent.addLocalMonitorForEvents(matching: .scrollWheel)
{ event in
    let scrollX = Float(event.scrollingDeltaX)
    InputController.shared.mouseScroll.x = scrollX
    let scrollY = Float(event.scrollingDeltaY)
    InputController.shared.mouseScroll.y = scrollY
    return event
  }
#endif
}
```

➤ Build and run the app. Zoom in using your track pad or mouse scroll wheel to get a view of the inside of the barn.

![Figure](Metal_by_Tutorials_v500mpdf/3bd9ad41fad5a6719a083469.png)

_Inside the barn_

Click and drag to orbit the barn. In Movement.swift, change Settings to suit your tracking preferences.

<a id="page-237"></a>

## **Orthographic Projection**

So far, you’ve created cameras with perspective so that objects further back in your 3D scene appear smaller than the ones closer to the camera. Orthographic projection flattens three dimensions to two dimensions without any perspective distortion.

![Figure](Metal_by_Tutorials_v500mpdf/51b634c3307479a09813e2c8.png)

_Orthographic projection_

<a id="page-238"></a>

Sometimes it’s a little difficult to see what’s happening in a large scene. To help with that, you’ll build a top-down camera that shows the whole scene without any perspective distortion.

➤ Open **Camera.swift**, and add a new camera:

```
struct OrthographicCamera: Camera, Movement {
  var transform = Transform()
  var aspect: CGFloat = 1
  var viewSize: CGFloat = 10
  var near: Float = 0.1
  var far: Float = 100

  var viewMatrix: float4x4 {
    (float4x4(translation: position) *
    float4x4(rotation: rotation)).inverse
  }
}
```

aspect is the ratio of the window’s width to height. viewSize is the unit size of the scene. You’ll calculate the projection frustum in the shape of a box.

➤ Add the projection matrix code:

```
var projectionMatrix: float4x4 {
  let rect = CGRect(
    x: -viewSize * aspect * 0.5,
    y: viewSize * 0.5,
    width: viewSize * aspect,
    height: viewSize)
  return float4x4(orthographic: rect, near: near, far: far)
}
```

<a id="page-239"></a>

Here, you calculate a rectangle for the front of the frustum using the view size and aspect ratio. Then you call the orthographic initializer defined in MathLibrary.swift with the frustum’s near and far values.

![Figure](Metal_by_Tutorials_v500mpdf/6d8957f012c8d444e84ad93a.png)

_The orthographic projection frustum_

➤ Add the method to update the camera when the view size changes:

```
mutating func update(size: CGSize) {
  aspect = size.width / size.height
}
```

This code sets the aspect ratio for the orthographic projection matrix.

<a id="page-240"></a>

➤ Add the frame update method:

```
mutating func update(deltaTime: Float) {
  let transform = updateInput(deltaTime: deltaTime)
  position += transform.position
  let input = InputController.shared
  let scrollSensitivity = Settings.mouseScrollSensitivity
  let zoom = input.mouseScroll.x * scrollSensitivity
    + input.mouseScroll.y * scrollSensitivity
  viewSize -= CGFloat(zoom)
  input.mouseScroll = .zero
}
```

Here, you use the previous Movement code to move around the scene using the WASD keys. You don’t need rotation, as you’re going to position the camera to be top-down. You use the mouse scroll to change the view size, which allows you to zoom in and out of the scene.

➤ Open **GameScene.swift** and change `camera` to:

`var camera = OrthographicCamera()`

➤ Replace the contents of `init()` with:

```
camera.position = [3, 2, 0]
camera.rotation.y = -.pi / 2
```

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/5cdded4e0c04cbdfefbc1bc0.png)

_Orthographic viewing from the front_

<a id="page-241"></a>

You’ll see a scene with no perspective. You might be surprised by this result. You can’t see the ground because there’s no field of view, which means you effectively “see” the ground plane side-on.

Replace the previous code in `init()` with:

```
camera.position = [0, 2, 0]
camera.rotation.x = .pi / 2
```

This code places the camera in a top-down rotation.

➤ Build and run the app. You can still move the WASD movement keys to move about the scene and use the mouse scroll to zoom out.

![Figure](Metal_by_Tutorials_v500mpdf/a9f605ca323dca2db91b9e29.png)

_Orthographic viewing from the top_

You’ll often use an orthographic camera when creating 2D games that look down on an entire board. Later, you’ll also use an orthographic camera when implementing shadows from directional lights.

<a id="page-242"></a>

## **Challenge**

For your challenge, combine FPCamera and ArcballCamera into one PlayerCamera. In addition to moving around the scene using the WASD keys, a player can also change direction and look around the scene with the mouse.

To achieve this:

• Copy FPCamera to PlayerCamera. This  sets position and rotation.

• Copy the left mouse down code from ArcballCamera’s update(deltaTime:) to the end of PlayerCamera‘s update(deltaTime:). This sets rotation when the mouse is used. PlayerCamera won’t use the scroll wheel for zooming.

• The view matrix should use rotation without the z axis because you always travel on the xy plane. So, replace PlayerCamera’s viewMatrix with:

```
var viewMatrix: float4x4 {
  let rotateMatrix = float4x4(
    rotationYXZ: [-rotation.x, rotation.y, 0])
  return (float4x4(translation: position) *
rotateMatrix).inverse
}
```

• Change the camera in GameScene and set its initial position.

When you finish, wander around your scene with your left hand on the keyboard to control forward motion and your right hand on the mouse to control direction. The left and right arrow keys will work for rotation, too.

![Figure](Metal_by_Tutorials_v500mpdf/a2826cfd6cf4a6560e8b66b2.png)

_Moving around the scene_

The challenge project contains extra code for iPadOS touch gestures instead of mouse or trackpad when using the ArcballCamera.

<a id="page-243"></a>

## **Key Points**

• Scenes abstract game code and scene setup away from the rendering code.

• Camera structures let you calculate the view and projection matrices separately from rendering the models.

• On macOS and iPadOS, use Apple’s GCController API to process input from game controllers, keyboards and mice.

• On iOS, GCVirtualController gives you onscreen D-pad controls.

• For a first-person camera, calculate position and rotation from the player’s perspective.

• An arcball camera orbits a target point.

• An orthographic camera renders without perspective so that all vertices rendered to the 2D screen appear at the same distance from the camera.

<a id="page-244"></a>

# 10

# Chapter 10: Lighting Fundamentals

Light and shade are important requirements for making your scenes pop. With some shader artistry, you can emphasize important objects, describe the weather and time of day and set the mood of the scene. Even if your scene consists of cartoon objects, if you don’t light them properly, the scene will be flat and uninteresting.

One of the simplest methods of lighting is the Phong reflection model. It’s named after Bui Tong Phong who published a paper in 1975 extending older lighting models. The idea is not to attempt duplication of light and reflection physics but to generate pictures that look realistic.

This model has been popular for over 40 years and is a great place to start learning how to fake lighting using a few lines of code. All computer images are fake, but there are more modern real-time rendering methods that model the physics of light.

In Chapter 11, “Maps &amp; Materials”, you’ll take a look at Physically Based Rendering (PBR), the lighting technique that your renderer will eventually use. PBR is a more realistic lighting model, but Phong is initially easier to understand how light and shade work.

<a id="page-245"></a>

## **The Starter Project**

➤ Open the starter project for this chapter.

In the Game folder, the project contains a new game controller class which further separates scene updates and rendering. Renderer is now independent from GameScene. GameController initializes and owns both Renderer and GameScene. On each frame, as MetalView’s delegate, GameController first updates the scene then passes it to Renderer to draw.

![Figure](Metal_by_Tutorials_v500mpdf/4a700ad9a7242ac9c1068569.png)

_Object ownership_

In GameScene.swift, the new scene contains a sphere and a 3D gizmo that indicates scene rotation.

DebugLights.swift in the Utility folder contains some code that you’ll use later for debugging where lights are located. Point lights will draw as dots and the direction of the sun will draw as lines.

<a id="page-246"></a>

➤ Familiarize yourself with the code, and build and run the project.

![Figure](Metal_by_Tutorials_v500mpdf/5ad18e07928565a0ba2f3f20.png)

_The starter app_

To rotate around the sphere and fully appreciate your lighting, the camera is an ArcballCamera type. Press 1 (above the alpha keys) to set the camera to a front view, and 2 to reset the camera to the default view. GameScene contains the key pressing code for this.

You can see that the sphere colors are very flat. In this chapter, you’ll add shading and specular highlights.

## **Representing Color**

In this book, you’ll learn the necessary basics to get you rendering light, color and simple shading. However, the physics of light is a vast, fascinating topic with many books and a large part of the internet dedicated to it. You can find further reading in references.markdown in the resources directory for this chapter.

In the real world, the reflection of different wavelengths of light is what gives an object its color. A surface that absorbs all light is black. Inside the computer world, pixels display color. The more pixels, the better the resolution and this makes the resulting image clearer. Each pixel is made up of subpixels. These are a predetermined single color, either red, green or blue. By turning on and off these subpixels, depending on the color depth, the screen can display most of the colors visible to the human eye.

<a id="page-247"></a>

In Swift, you can represent a color using the RGB values for that pixel. For example, float3(1, 0, 0) is a red pixel, float3(0, 0, 0) is black and float3(1, 1, 1) is white.

From a shading point of view, you can combine a red surface with a gray light by multiplying the two values together:

`let result = float3(1.0, 0.0, 0.0) * float3(0.5, 0.5, 0.5)`

The result is `(0.5, 0, 0)`, which is a darker shade of red.

![Figure](Metal_by_Tutorials_v500mpdf/ebfae51456a632408021bd53.png)

_Color shading_

For simple Phong lighting, you can use the slope of the surface. The more the surface slopes away from a light source, the darker the surface becomes.

![Figure](Metal_by_Tutorials_v500mpdf/92bf2d7b98c9ba64d4dd09b2.png)

_A 3D shaded sphere_

<a id="page-248"></a>

## **Normals**

The slope of a surface can determine how much a surface reflects light.

In the following diagram, point A is facing straight toward the sun and will receive the most amount of light; point B is facing slightly away but will still receive some light; point C is facing entirely away from the sun and shouldn’t receive any of the light.

![Figure](Metal_by_Tutorials_v500mpdf/b1dccbd09a264b1217ea03dc.png)

_Surface normals on a sphere_

Note: In the real world, light bounces from surface to surface; if there’s any light in the room, there will be some reflection from objects that gently lights the back surfaces of all the other objects. This is global illumination. The Phong lighting model lights each object individually and is called local illumination.

The dotted lines in the diagram are tangent to the surface. A tangent line is a straight line that best describes the slope of the curve at a point.

The lines coming out of the circle are at right angles to the tangent lines. These are called surface normals, and you first encountered these in Chapter 7, “The Fragment Function”.

<a id="page-249"></a>

## **Light Types**

There are several standard light options in computer graphics, each of which has their origin in the real world.

• Directional Light: Sends light rays in a single direction. The sun is a directional light.

• Point Light: Sends light rays in all directions like a light bulb.

• Spotlight: Sends light rays in limited directions defined by a cone. A flashlight or a desk lamp would be a spotlight.

## **Directional Light**

A scene can have many lights. In fact, in studio photography, it would be highly unusual to have just a single light. By putting lights into a scene, you control where shadows fall and the level of darkness. You’ll add several lights to your scene through the chapter.

The first light you’ll create is the sun. The sun is a point light that puts out light in all directions, but for computer modeling, you can consider it a directional light. It’s a powerful light source a long way away. By the time the light rays reach the earth, the rays appear to be parallel. Check this outside on a sunny day — everything you can see has its shadow going in the same direction.

![Figure](Metal_by_Tutorials_v500mpdf/0dd220fb9cdbce8c84f453a4.png)

_The direction of sunlight_

<a id="page-250"></a>

To define the light types, you’ll create a Light structure that both the GPU and the CPU can read, and a SceneLighting structure that will describe the lighting for GameScene.

➤ In the Shaders folder, open Common.h, and before #endif, create an enumeration of the light types you’ll be using:

```
typedef enum {
  unused = 0,
  Sun = 1,
  Spot = 2,
  Point = 3,
  Ambient = 4
} LightType;
```

➤ Under this, add the structure that defines a light:

```
typedef struct {
  LightType type;
  vector_float3 position;
  vector_float3 color;
  float intensity;
  vector_float3 specularColor;
  float radius;
  vector_float3 attenuation;
  float coneAngle;
  vector_float3 coneDirection;
  float coneAttenuation;
} Light;
```

This structure holds the position, color and intensity of the light. You’ll learn about the other properties as you go through the chapter.

➤ Create a new Swift file in the Game folder, and name it SceneLighting.swift. Then, add this code:

```
struct SceneLighting {
  static func buildDefaultLight() -> Light {
    var light = Light()
    light.position = [0, 0, 0]
    light.color = [1, 1, 1]
    light.intensity = 1.0
    light.specularColor = [0.6, 0.6, 0.6]
    light.attenuation = [1, 0, 0]
    light.type = Sun
    return light
  }
}
```

<a id="page-251"></a>

This file will hold the lighting for GameScene. You’ll have several lights, and buildDefaultLight() will create a basic light.

➤ Create a property in `SceneLighting` for a sun directional light:

```
let sunlight: Light = {
  var light = Self.buildDefaultLight()
  light.position = [1, 2, -2]
  return light
}()
```

position for a directional light is actually the direction from the surface to the light. There is no world position for a directional light, as the vector is infinite. The direction is to the right of the scene, and forward of the sphere. The sphere is placed at the world’s origin.

➤ Create an array to hold the various lights you’ll be creating shortly:

`var lights: [Light] = []`

➤ Add the initializer:

```
init() {
  lights.append(sunlight)
}
```

You’ll add all your lights for the scene in the initializer.

➤ Open GameScene.swift, and add the lighting property to GameScene:

`let lighting = SceneLighting()`

You’ll do all the light shading in the fragment function so you’ll need to pass the array of lights to that function. Metal Shading Language doesn’t have a dynamic array feature, and there is no way to find out the number of items in an array. You’ll pass this value to the fragment shader in Params.

➤ Open Common.h, and add these properties to Params:

```
uint32_t lightCount;
vector_float3 cameraPosition;
```

You’ll need the camera position property later.

While you’re in Common.h, add a new index to BufferIndices:

`LightBuffer = 13`

<a id="page-252"></a>

You’ll use this to send lighting details to the fragment function.

➤ Open Renderer.swift, and add this to updateUniforms(scene:):

`params.lightCount = UInt32(scene.lighting.lights.count)`

You’ll be able to access this value in the fragment shader function.

➤ In `draw(scene:in:)`, just before `for model in scene.models`, add this:

```
var lights = scene.lighting.lights
renderEncoder.setFragmentBytes(
  &lights,
  length: MemoryLayout<Light>.stride * lights.count,
  index: LightBuffer.index)
```

Here, you send the array of lights to the fragment function in buffer index 13.

You’ve now set up a sun light on the Swift side. You’ll do all the actual light calculations in the fragment function, and you’ll find out more about light properties.

## The Phong Reﬂection Model

In the Phong reflection model, there are three types of light reflection. You’ll calculate each of these, and then add them up to produce a final color.

![Figure](Metal_by_Tutorials_v500mpdf/f0483ea9297b9bc6fe9f46a8.png)

_Diffuse shading and micro-facets_

<a id="page-253"></a>

• Diffuse: In theory, light coming at a surface bounces off at an angle reflected about the surface normal at that point. However, surfaces are microscopically rough, so light bounces off in all directions as the picture above indicates. This bouncing results in a diffuse color where the light intensity is proportional to the angle between the incoming light and the surface normal. In computer graphics, this model is called Lambertian reflectance named after Johann Heinrich Lambert who died in 1777. In the real world, this diffuse reflection is generally true of dull, rough surfaces, but the surface with the most Lambertian property is human-made: Spectralon (https://en.wikipedia.org/wiki/Spectralon), which is used for optical components.

• Specular: The smoother the surface, the shinier it is, and the light bounces off the surface in fewer directions. A mirror completely reflects off the surface normal without deflection. Shiny objects produce a visible specular highlight, and rendering specular lighting can give your viewers hints about what sort of surface an object is — whether a car is an old wreck or fresh off the sales lot.

• Ambient: In the real-world, light bounces around all over the place, so a shadowed object is rarely entirely black. This is the ambient reflection.

A surface color is made up of an emissive surface color plus contributions from ambient, diffuse and specular. For diffuse and specular, to find out how much light the surface should receive at a particular point, all you have to do is find out the angle between the surface-to-light direction and the surface normal.

## **The Dot Product**

Fortunately, there’s a straightforward mathematical operation to discover the angle between two vectors called the dot product.

![Figure](Metal_by_Tutorials_v500mpdf/1b8841edcbd9b26c98f60e4e.png)

And:

![Figure](Metal_by_Tutorials_v500mpdf/7bc840e7e4982ffbd2f91529.png)

Where `||A||` means the length (or magnitude) of vector A.

Even more fortunately, both simd and Metal Shading Language have a function dot() to get the dot product, so you don’t have to remember the formulas.

As well as finding out the angle between two vectors, you can use the dot product for checking whether two vectors are pointing in the same direction.

<a id="page-254"></a>

Resize the two vectors into unit vectors — that’s vectors with a length of 1. You can do this using the normalize() function. If the unit vectors are parallel with the same direction, the dot product result will be 1. If they are parallel but opposite directions, the result will be -1. If they are at right angles (orthogonal), the result will be 0.

![Figure](Metal_by_Tutorials_v500mpdf/cb2c27db650ea92895b3ca80.png)

_The dot product_

For calculating how much light should be at a certain point on the surface, you take the dot product of the direction of the light from the surface and the surface normal.

If the direction vector to the sun is pointing straight up, and the blue (normal) vector is also pointing straight up, the dot product will be 1 (fully lit). This value is the cosine angle between the two vectors. The great thing about cosines is that they are always values between -1 and 1 so you can use this range to determine how bright the light should be at a certain point.

Take the following example:

![Figure](Metal_by_Tutorials_v500mpdf/df1b0cd71dd7f9b0aa0719d4.png)

_The dot product of sunlight and normal vectors_

The direction vector to the sun is [-2, 2, 0]. Vector A is a normal vector of [-2, 2, 0]. The two vectors are pointing in the same direction, so when you turn the vectors into unit vectors (normalize them), the dot product of them will be 1 (fully lit).

<a id="page-255"></a>

Vector B is a normal vector of [0.3, 2, 0]. Sunlight is a directional light, so take the same direction vector of [-2, 2, 0]. Sunlight and B when normalized have a dot product of 0.59 (partially lit).

In the fragment shader, you’ll be able to take these values and multiply the fragment color by the dot product to get the brightness of the fragment.

## Diffuse Reﬂection

Shading from the sun does not depend on where the camera is. When you rotate the scene, you’re rotating the world, including the sun. The sun’s position will be in world space, and you’ll put the model’s normals into the same world space to be able to calculate the dot product against the sunlight direction. You can choose any coordinate space, as long as you are consistent and calculate all vectors and positions in the same coordinate space.

To be able to assess the slope of the surface in the fragment function, you’ll reposition the normals in the vertex function in much the same way as you repositioned the vertex position earlier. You’ll add the normals to the vertex descriptor so that the vertex function can process them.

➤ Open ShaderDefs.h, and add these properties to VertexOut:

```
float3 worldPosition;
float3 worldNormal;
```

These will hold the vertex position and vertex normal in world space.

Calculating the new position of normals is a bit different from the vertex position calculation. MathLibrary.swift contains a matrix method to create a normal matrix from another matrix. This normal matrix is a 3×3 matrix, because firstly, you’ll do lighting in world space which doesn’t need projection, and secondly, translating an object does not affect the slope of the normals. Therefore, you don’t need the fourth W dimension. However, if you scale an object in one direction (non-linearly), then the normals of the object are no longer orthogonal and this approach won’t work. As long as you decide that your engine does not allow non-linear scaling, then you can use the upper-left 3×3 portion of the model matrix, and that’s what you’ll do here.

➤ Open Common.h and add this matrix property to Uniforms:

`matrix_float3x3 normalMatrix;`

This will hold the normal matrix in world space.

<a id="page-256"></a>

➤ In the Renderer folder, open Rendering.swift, and in render(encoder:uniforms:params:), add this after setting uniforms.modelMatrix:

`uniforms.normalMatrix = uniforms.modelMatrix.upperLeft`

This creates the normal matrix from the model matrix.

➤ Open **Vertex.metal**, and in `vertex_main`, after assigning `position`, add this:

`float4 worldPosition = uniforms.modelMatrix * in.position;`

You hold the vertex’s world position before converting to camera and projection space.

➤ When defining `out`, populate the `VertexOut` properties:

```
.worldPosition = worldPosition.xyz / worldPosition.w,
.worldNormal = uniforms.normalMatrix * in.normal
```

The rasterizer performs the perspective divide on position, as described in Chapter 6, “Coordinate Spaces”. To ensure any scaling is taken care of, you perform the divide by w on worldPosition here.

Earlier in the chapter, you sent Renderer’s lights array to the fragment function in the LightBuffer index, but you haven’t yet changed the fragment function to receive the array.

➤ Open Fragment.metal and add this to fragment\_main’s parameter list:

`constant Light *lights [[buffer(LightBuffer)]],`

## **Creating Shared Functions in C++**

Often you’ll want to access C++ functions from multiple files. Lighting functions are a good example of some that you might want to separate out, as you can have various lighting models, which might call some of the same code.

To call a function from multiple **.metal** files:

1. Set up a header file with the name of the functions that you’re going to create.

2. Create a new .metal file and import the header, and also the bridging header file Common.h if you’re going to use a structure from that file.

<a id="page-257"></a>

3. Create the lighting functions in this new file.

4. In your existing .metal file, import the new header file and use the lighting functions.

➤ In the Shaders folder, create a new Header File called Lighting.h. Don’t add it to the target.

➤ Add this function header before #endif /\* Lighting\_h \*/:

```
#import "Common.h"

float3 phongLighting(
  float3 normal,
  float3 position,
  constant Params &params,
  constant Light *lights,
  float3 baseColor);
```

Here, you define a C++ function that will return a float3.

➤ Still in the Shaders folder, create a new Metal File called Lighting.metal. Add it to the target.

➤ Add this new function:

```
#import "Lighting.h"

float3 phongLighting(
  float3 normal,
  float3 position,
  constant Params &params,
  constant Light *lights,
  float3 baseColor) {
    return float3(0);
}
```

You create a new function that returns a zero float3 value. You’ll build up code in phongLighting to calculate this final lighting value.

➤ Open **Fragment.metal**, and replace `#import "Common.h"` with:

`#import "Lighting.h"`

Now you’ll be able to use `phongLighting` within this file.

➤ In `fragment_main`, replace `return float4(baseColor, 1);` with this:

`float3 normalDirection = normalize(in.worldNormal);`

<a id="page-258"></a>

```
float3 color = phongLighting(
  normalDirection,
  in.worldPosition,
  params,
  lights,
  baseColor
);
return float4(color, 1);
```

Here, you make the world normal a unit vector, and call the new lighting function with the necessary parameters.

If you build and run the app now, your models will render in black, as that’s the color that you’re currently returning from phongLighting.

![Figure](Metal_by_Tutorials_v500mpdf/2120ae7f9c3f8d621392ae80.png)

_No lighting_

➤ Open **Lighting.metal**, and replace `return float3(0);` with:

```
float3 diffuseColor = 0;
float3 ambientColor = 0;
float3 specularColor = 0;
for (uint i = 0; i < params.lightCount; i++) {
  Light light = lights[i];
  float3 surfaceColor = light.color * light.intensity *
baseColor;
  switch (light.type) {
    case Sun: {
      break;
    }
    case Point: {
      break;
    }
    case Spot: {
      break;
    }
    case Ambient: {
```

<a id="page-259"></a>

```
      break;
    }
    case unused: {
      break;
    }
  }
}
return diffuseColor + specularColor + ambientColor;
```

This sets up the outline for all the lighting calculations you’ll do to accumulate the final fragment color, made up of diffuse, specular and ambient contributions. You’ll adjust surfaceColor for each light type.

➤ Above `break` in `case Sun`, add the following code:

```
// 1
float3 lightDirection = normalize(light.position);
// 2
float diffuseIntensity =
  saturate(dot(lightDirection, normal));
// 3
diffuseColor += surfaceColor * diffuseIntensity;
```

Going through this code:

1. lightDirection is a unit vector from the surface to the light.

2. You calculate the dot product of the two vectors. When the fragment fully points toward the light, the dot product will be 1. saturate makes sure the value is between 0 and 1 by clamping negative numbers. This gives you the slope of the surface, and therefore the intensity of the diffuse factor.

3. Multiply the surface color by the diffuse intensity to get the diffuse shading. If you have several sun lights, diffuseColor will accumulate the diffuse shading.

<a id="page-260"></a>

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/39a06ecd172546c7bb6434a1.png)

_Diffuse shading_

You can sanity-check your results by returning your intermediate calculations from phongLighting. The following image shows normal and diffuseIntensity from the front view.

![Figure](Metal_by_Tutorials_v500mpdf/f7deeff4257541a7a09ecbd8.png)

_Visualizing the normal and diffuse intensity_

Note: To get the front view in your app, press “1” above the alpha keys while running it. “2” will reset to the default view.

DebugLights.swift and DebugLights.metal in the Utility folder, have some debugging methods so that you can visualize where your lights are.

➤ Open **DebugLights.swift**, and remove `/*` and `*/` at the top and bottom of the file.

Before you added code in this chapter, this file would not compile, but does now.

<a id="page-261"></a>

➤  Open Renderer.swift, and toward the end of draw(scene:in:), before renderEncoder.endEncoding(), add this:

```
DebugLights.draw(
  lights: scene.lighting.lights,
  encoder: renderEncoder,
  uniforms: uniforms)
```

This code will display lines to visualize the direction of the sun light.

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/a03dc551449623c0f77f4030.png)

_Debugging sunlight direction_

The red lines show the parallel sun light direction vector. As you rotate the scene, you can see that the brightest parts are the ones facing towards the sun.

Note: the debug method uses .line  as the rendering type. Unfortunately line width is not configurable on the GPU, so the lines may disappear at certain angles when they are too thin to render.

This shading is pleasing, but not accurate. Take a look at the back of the sphere. The back of the sphere is black; however, you can see that the top of the green surround is bright green because it’s facing up. In the real-world, the surround would be blocked by the sphere and so be in the shade. However, you’re currently not taking occlusion into account, and you won’t be until you master shadows in Chapter 13, “Shadows”.

<a id="page-262"></a>

## Ambient Reﬂection

In the real-world, colors are rarely pure black. There’s light bouncing about all over the place. To simulate this, you can use ambient lighting. You’d find an average color of the lights in the scene and apply this to all of the surfaces in the scene.

➤ Open **SceneLighting.swift**, and add an ambient light property:

```
let ambientLight: Light = {
  var light = Self.buildDefaultLight()
  light.color = [0.05, 0.2, 0]
  light.type = Ambient
  return light
}()
```

This light is a slightly green tint.

➤ Add this to the end of init():

`lights.append(ambientLight)`

➤ Open **Lighting.metal**, and above `break` in `case Ambient`, add this:

`ambientColor += surfaceColor;`

➤ Build and run the app. The scene is now tinged green as if there is a green light being bounced around.

![Figure](Metal_by_Tutorials_v500mpdf/8ac1fc82ff7792fe749ebc2d.png)

_Ambient lighting_

<a id="page-263"></a>

## Specular Reﬂection

The final component of the Phong reflection model is the specular reflection. This is your chance to put a coat of shiny varnish on the sphere. The specular highlight depends upon the position of the observer. If you pass a shiny car, you’ll only see the highlight at certain angles.

![Figure](Metal_by_Tutorials_v500mpdf/9296f7a3589bb025ef4edb70.png)

_Specular reflection_

The light direction vector (L) reflects (R) about the normal (N). If the viewer (V) is within a particular cone around the reflection (R), then the viewer will see the specular highlight. That cone is an exponential shininess parameter. The shinier the surface is, the smaller and more intense the specular highlight.

In your case, the viewer is your camera so you’ll need to pass the camera coordinates, again in world position, to the fragment function. Earlier, you set up a cameraPosition property in params, and this is what you’ll use to pass the camera position.

➤ Open **Renderer.swift**, and in `updateUniforms(scene:)`, add this:

`params.cameraPosition = scene.camera.position`

scene.camera.position is already in world space, and you’re already passing params to the fragment function, so you don’t need to take further action here.

<a id="page-264"></a>

➤ Open Lighting.metal, and in phongLighting, add the following variables to the top of the function:

```
float materialShininess = 32;
float3 materialSpecularColor = float3(1, 1, 1);
```

These hold the surface material properties of a shininess factor and the specular color. As these are surface properties, you should be getting these values from each model’s materials, and you’ll do that in the following chapter.

➤ Above `break` in `case Sun`, add the following:

```
if (diffuseIntensity > 0) {
  // 1 (R)
  float3 reflection =
      reflect(-lightDirection, normal);
  // 2 (V)
  float3 viewDirection =
      normalize(params.cameraPosition - position);
  // 3
  float specularIntensity =
      pow(saturate(dot(reflection, viewDirection)),
          materialShininess);
  specularColor +=
      light.specularColor * materialSpecularColor
        * specularIntensity;
}
```

Going through this code:

1. For the calculation of the specular color, you’ll need (L)ight, (R)eflection, (N)ormal and (V)iew. You already have (L) and (N), so here you use the Metal Shading Language function reflect to get (R).

2. You need the view vector between the fragment and the camera for (V).

3. Now you calculate the specular intensity. You find the angle between the reflection and the view using the dot product, clamp the result between 0 and 1 using saturate, and raise the result to a shininess power using pow. You then use this intensity to work out the specular color for the fragment.

<a id="page-265"></a>

➤ Build and run the app to see your completed lighting.

![Figure](Metal_by_Tutorials_v500mpdf/d28f38f047010eefbec616ca.png)

_Specular reflection_

Experiment with changing materialShininess from 8 to 512. In Chapter 11, “Maps &amp; Materials”, you’ll find out how to read in material and texture properties from the model to change its color and lighting and create a more realistic render.

Next, you’ll add more variety to your scene with point and spot lights.

## **Point Lights**

As opposed to the sun light, where you converted the position into parallel direction vectors, point lights shoot out light rays in all directions.

![Figure](Metal_by_Tutorials_v500mpdf/567bf6aec8e5346cf268980d.png)

_Point light direction_

<a id="page-266"></a>

A light bulb will only light an area of a certain radius, beyond which everything is dark. So you’ll also specify attenuation where a ray of light doesn’t travel infinitely far.

![Figure](Metal_by_Tutorials_v500mpdf/78cdab6544f1ce533db32d21.png)

_Point light attenuation_

Light attenuation can occur abruptly or gradually. The original OpenGL formula for attenuation is:

![Figure](Metal_by_Tutorials_v500mpdf/b142e84b4ca057f92458102e.png)

Where x is the constant attenuation factor, y is the linear attenuation factor and z is the quadratic attenuation factor.

The formula gives a curved fall-off. You’ll represent xyz with a float3. No attenuation at all will be float3(1, 0, 0) — substituting x, y and z into the formula results in a value of 1.

➤ Open SceneLighting.swift, and add a point light property to SceneLighting:

```
let redLight: Light = {
  var light = Self.buildDefaultLight()
  light.type = Point
  light.position = [-0.8, 0.76, -0.18]
  light.color = [1, 0, 0]
  light.attenuation = [0.2, 0.8, 1.0]
  return light
}()
```

<a id="page-267"></a>

Here, you create a red point light with a position and attenuation. You can experiment with the attenuation values to change radius and fall-off.

➤ Add the light to lights in init():

`lights.append(redLight)`

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/a5c8e7c94ade557c721ffbae.png)

_Debugging a point light_

You’ll see a small red dot which marks the position of the point light rendered by DebugLights.

Note: The shader for the point light debug dot is worth looking at. In DebugLights.metal, in fragment\_debug\_point, the default square point is turned into a circle by discarding fragments greater than a certain radius from the center of the point.

The debug lights function shows you where the point light is, but it doesn’t produce any light yet. You’ll do this in the fragment shader.

➤ Open Lighting.metal, and in phongLighting, add this above break in case Point:

```
// 1
float d = distance(light.position, position);
// 2
float3 lightDirection = normalize(light.position - position);
// 3
float attenuation = 1.0 / (light.attenuation.x +
    light.attenuation.y * d + light.attenuation.z * d * d);
```

<a id="page-268"></a>

```
float diffuseIntensity =
    saturate(dot(lightDirection, normal));
float3 color = surfaceColor * diffuseIntensity;
// 4
color *= attenuation;
diffuseColor += color;
```

Going through this code:

1. You find out the distance between the light and the fragment position.

2. With the directional sun light, you used light position as the surface-to-light direction. Here, you calculate the direction from the fragment position to the light position.

3. Calculate the attenuation using the attenuation formula and the distance to see how bright the fragment will be.

4. After calculating the diffuse color as you did for the sun light, multiply this color by the attenuation.

➤ Build and run the app, and you’ll see the full effect of the red point light.

![Figure](Metal_by_Tutorials_v500mpdf/680e323196fff2cb625f1cb6.png)

_Rendering a point light_

Remember the sphere is slightly green because of the ambient light.

## **Spotlights**

The last type of light you’ll create in this chapter is the spotlight. This sends light rays in limited directions. Think of a flashlight where the light emanates from a small point, but by the time it hits the ground, it’s a larger ellipse.

<a id="page-269"></a>

You define a cone angle to contain the light rays with a cone direction. You also define a cone power to control the attenuation at the edge of the ellipse.

![Figure](Metal_by_Tutorials_v500mpdf/0f99e0967b05e16fb62f62e5.png)

_Spotlight angle and attenuation_

➤ Open **SceneLighting.swift**, and add a new light:

```
lazy var spotlight: Light = {
  var light = Self.buildDefaultLight()
  light.type = Spot
  light.position = [-0.64, 0.64, -1.07]
  light.color = [1, 0, 1]
  light.attenuation = [0.2, 0.4, 0.2]
  light.coneAngle = Float(40).degreesToRadians
  light.coneDirection = [0.5, -0.7, 1]
  light.coneAttenuation = 20
  return light
}()
```

This light is similar to the point light with the added cone angle, direction and cone attenuation.

➤ Add the light to lights in init():

`lights.append(spotlight)`

➤ Open Lighting.metal, and in phongLighting, add this code above break in case Spot:

```
// 1
float d = distance(light.position, position);
float3 lightDirection = normalize(light.position - position);
// 2
float3 coneDirection = normalize(light.coneDirection);
float spotResult = dot(lightDirection, -coneDirection);
// 3
```

<a id="page-270"></a>

```
if (spotResult > cos(light.coneAngle)) {
  float attenuation = 1.0 / (light.attenuation.x +
      light.attenuation.y * d + light.attenuation.z * d * d);
  // 4
  attenuation *= pow(spotResult, light.coneAttenuation);
  float diffuseIntensity =
           saturate(dot(lightDirection, normal));
  float3 color = surfaceColor * diffuseIntensity;
  color *= attenuation;
  diffuseColor += color;
}
```

This code is very similar to the point light code. Going through the comments:

1. Calculate the distance and direction as you did for the point light. This ray of light may be outside of the spot cone.

2. Calculate the cosine angle (that’s the dot product) between that ray direction and the direction the spot light is pointing.

3. If that result is outside of the cone angle, then ignore the ray. Otherwise, calculate the attenuation as for the point light. Vectors pointing in the same direction have a dot product of 1.0.

4. Calculate the attenuation at the edge of the spot light using coneAttenuation as the power.

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/04575a27f1f6fc38f24a1b45.png)

_Rendering a spotlight_

Experiment with changing the various attenuations.  A cone angle of 5º with attenuation of (0.5, 0, 0) and a cone attenuation of 500 will produce a very small targeted soft light; whereas a cone angle of 20º with a cone attenuation of 1 will produce a sharp-edged round light.

<a id="page-271"></a>

## **Key Points**

• Shading is the reason why objects don’t look flat. Lights provide illumination from different directions.

• Normals describe the slope of the curve at a point. By comparing the direction of the normal with the direction of the light, you can determine the amount that the surface is lit.

• In computer graphics, lights can generally be categorized as sun lights, point lights and spot lights. In addition, you can have area lights and surfaces can emit light. These are only approximations of real-world lighting scenarios.

• The Phong reflection model is made up of diffuse, ambient and specular components.

• Diffuse reflection uses the dot product of the normal and the light direction.

• Ambient reflection is a value added to all surfaces in the scene.

• Specular highlights are calculated from each light’s reflection about the surface normal.

## **Where to Go From Here?**

You’ve covered a lot of lighting information in this chapter. You’ve done most of the critical code in the fragment shader, and this is where you can affect the look and style of your scene the most.

You’ve done some weird and wonderful calculations by working out dot products between surface normals and various light directions. The formulas you used in this chapter are a small cross-section of computer graphics research that various brilliant mathematicians have come up with over the years. If you want to read more about lighting, you’ll find some interesting internet sites listed in references.markdown in the resources folder for this chapter.

In the next chapter, you’ll change the lighting model to physically based, and find out how you can change how a surface looks with texture maps and materials.

<a id="page-272"></a>

# **Section II: Intermediate Metal**

With the basics under your belt, you can move on to multi-pass rendering. You’ll add shadows and learn several new rendering techniques. Programming the GPU using compute shaders can be intimidating, so you’ll create particle systems to learn how fast multi-threaded solutions can be.

<a id="page-273"></a>

# 11

# Chapter 11: Maps &amp; Materials

In the previous chapter, you set up a simple Phong lighting model. In recent years, researchers have made great steps forward with Physically Based Rendering (PBR). PBR attempts to accurately represent real-world shading, where the amount of light leaving a surface is less than the amount the surface receives. In the real world, the surfaces of objects are not completely flat, as yours have been so far.

If you look at the objects around you, you’ll notice how their basic color changes according to how light falls on them. Some objects have a smooth surface, and some have a rough surface. Heck, some might even be shiny metal! Take for example, this sphere with a brick texture. The render on the left shows a simple color texture with Phong shading. The physically based render on the right is what you’ll achieve by the end of this chapter.

![Figure](Metal_by_Tutorials_v500mpdf/56c4e2efc0737bd143ec4c1e.png)

_PBR render_

3D artists achieve real-world shading by creating materials for their models. Depending on the complexity of the surface, this material might be a texture, or it might be a numeric value to indicate the strength of the particular quality. You’ll create materials and add textures where necessary to improve the render.

<a id="page-274"></a>

## **Physically Based Rendering (PBR)**

As its name suggests, PBR attempts physically realistic interaction of light with surfaces. Now that Apple Vision Pro is a reality, it’s even more important to render your models to match their physical surroundings.

Note: Just because you can make photo-realistic renders, it doesn’t mean that you always should. Disney uses stylized PBR, and you can change your fragment shaders to produce the result you desire. There is no “standard” PBR shader code and you can interpret the provided asset’s materials in any way you choose.

The general principles of PBR are:

• Surfaces should not reflect more light than they receive.

• Surfaces can be described with known, measured physical properties.

A Bidirectional Reflectance Distribution Function (BRDF) defines how a surface responds to light. There are various highly mathematical BRDF models for both diffuse and specular, but the most common are Lambertian diffuse; and for the specular, variations on the Cook-Torrance model (presented at SIGGRAPH 1981). This takes into account:

• micro-facet slope distribution: The previous chapter briefly covered micro-facets and how light bounces off surfaces in many directions.

• Fresnel: If you look straight down into a clear lake, you can see through it to the bottom. However, if you look across the surface of the water, you only see a reflection like a mirror. This is the Fresnel effect, where the reflectivity of the surface depends upon the viewing angle.

• geometric attenuation: Self-shadowing of the micro-facets.

Each of these components have different approximations, or models written by many clever people. It’s a vast and complex topic. In the resources folder for this chapter, references.markdown contains a few places where you can learn more about physically based rendering and the calculations involved. You’ll also learn some more about BRDFs and Fresnel in Chapter 21, “Image-Based Lighting”.

<a id="page-275"></a>

## **Common PBR Material Properties**

Poly Haven (https://polyhaven.com) has some great 3D assets and textures. For example, this alarm clock model:

![Figure](Metal_by_Tutorials_v500mpdf/34c4f2216bf6c7dc19c5c150.png)

_An alarm clock_

For this model, the artist created textures for the five most common material properties used in PBR lighting models:

![Figure](Metal_by_Tutorials_v500mpdf/0935475c0244c1b1d9e1e3e9.png)

_Common texture maps_

These properties can be either a texture or a value.

• Diffuse Color (Albedo): Albedo is originally an astronomical term describing the measurement of diffuse reflection of solar radiation, but it has come to mean in computer graphics the surface color without any shading applied to it. Diffuse color may have some shading built into the texture. You already met diffuse color in the form of the base color map.

• Normal: A texture can override vertex normal values and distort lit fragments for extra surface detail.

• Roughness: A grayscale value that indicates the shininess of a surface. White is rough, and black is smooth. If you have a scratched shiny surface, a roughness texture might consist of mostly black or dark gray with light gray scratch marks.

<a id="page-276"></a>

• Metallic: A surface is either a conductor of electricity — in which case it’s a metal; or it isn’t a conductor — in which case it’s a dielectric. Most metallic textures consist of 0 (black) and 1 (white) values only: 0 for dielectric and 1 for metal.

• Ambient Occlusion (AO): AO defines how much light reaches a surface. For example, less light will reach nooks and crannies. You multiply the diffuse color with the AO value, so the default value is 1, AO textures are grayscale and can enhance the look of shadowing.

When you write a PBR lighting shader, for each fragment, you want to achieve values for diffuse color and specular color. You derive color from diffuse color, metallic and AO. You include the roughness value in the mix to achieve the specular color.

Complex renderers can use many other material properties, but for now, you’ll only include these in your materials.

## **The Starter App**

➤ In Xcode, open the starter project for this chapter.

➤ Build and run the app, and you’ll see final-sphere.usdz rendered with Phong shading. The sphere has a color texture, but the result is flat and uninteresting.

![Figure](Metal_by_Tutorials_v500mpdf/b394f7106f62f916d02686bc.png)

_A sphere with color texture_

There are two lights in the scene - a sun light and an ambient light. The code is the almost same as at the end of the previous chapter with the exception of GameScene and SceneLighting, which simply set up the different model and lighting.

<a id="page-277"></a>

Lighting.metal reduces the amount of specular highlight. Pressing keys “1” and “2” take you to the front and default views respectively.

Because PBR shading is quite mathematically challenging, Lighting.h and PBR.metal contain three functions, currently commented out, that calculate the diffuse, specular and ambient colors. There are many different PBR shading models, but this specular lighting is a modified Cook-Torrance model. (R.L. Cook and K.E. Torrance came up with it in 1982.)

## Examining USD Files in Reality Composer Pro

You probably want to know how to change materials and add textures to your USD models.

Apple provides Reality Composer Pro for designing RealityKit and VisionOS content. You can load in USD files and create a scene, and then export that scene out to a new USD file. Whereas you create models in Blender, you assemble scenes containing these models in Reality Composer Pro. If you want to discover more about Reality Composer Pro, Apple has documented a full walkthrough (https:// developer.apple.com/documentation/visionos/designing-realitykit-content-with-reality-composer-pro).

➤ In Xcode, choose the Menu option Xcode &gt; Open Developer Tool &gt; Reality Composer Pro.

➤ Create a new **Project** called **Sphere**, and save the file so that you can find it again.

<a id="page-278"></a>

![Figure](Metal_by_Tutorials_v500mpdf/dc9085c0851f2f3e79cc33cf.png)

_The Sphere project_

➤ From your Xcode project, drag starter-sphere.usdz into the Project Browser located under the scene view.  assembly panel. Then drag the sphere to the Scene Navigator located on the left of the scene view. With the sphere selected, press Command-F to bring the sphere into frame.

These are the controls to navigate the scene:

• Click and drag on the background to look around the scene.

• Command-Click and drag on the background to pan.

• Option-Click and drag on the background to zoom in and out (or use the trackpad zoom gesture or mouse scroll wheel).

• You can also use the icons at the bottom of the scene view.

➤ Click on the sphere to select it, and in the Inspector, set the Transform Position to zero.

<a id="page-279"></a>

➤ In the Scene Hierarchy, Option-Click Root to see all the elements of the model, then select brick to see the sphere’s material in the Inspector.

![Figure](Metal_by_Tutorials_v500mpdf/1feb72b9068957bbd558158e.png)

_Reality Composer Pro Material_

Reality Composer Pro shows you all the material properties available to RealityKit renders. The sphere’s diffuse color is overridden by the brick texture. Next to each material property value is a download icon where you can add textures to the model.

This model has only one material, but, as you’ll see later, models can have multiple materials for different parts of the model’s geometry.

➤ Locate the **resources** folder for this chapter. You’ll find three textures:

• brick-color.png: The diffuse color texture.

• brick-roughness.png: This describes how shiny the sphere’s surface is.

• brick-normal.png: The normal map is more complex, and you’ll learn more about distorting normals later in the chapter.

➤ Drag brick-roughness.png to the Roughness download icon in Reality Composer Pro, and brick-normal.png to the Normal download icon. For each texture, check the difference in the appearance of the model in the scene.

<a id="page-280"></a>

![Figure](Metal_by_Tutorials_v500mpdf/eb3819cdda4fa66656ec2ffa.png)

_Color, roughness and normal textures applied_

The Reality-rendered sphere looks quite different with these textures applied. Now to find out how to do this in your own renders.

Note: if you wish to use your own .usdz file exported from Reality Composer Pro, choose the Menu option File &gt; Export. Save your project, and then save the .usdz file as final-sphere.usdz. The starter project already contains this model.

## **Materials**

Before adding more textures to your render, you’ll set up the basic default material values, so that your PBR shader can get to work.

➤ In Xcode, open **Common.h**, and add a new structure to hold material values:

```
typedef struct {
  vector_float3 baseColor;
  float roughness;
  float metallic;
  float ambientOcclusion;
} Material;
```

As you’ve seen, there are more material properties available to a physically based shader, but these are the most common. The normal value is provided by the vertex buffers.

<a id="page-281"></a>

➤ Open Submesh.swift, and create a new property in Submesh under textures to hold the submesh’s material:

`var material: Material`

Your project won’t compile until you’ve initialized material.

➤ At the bottom of Submesh.swift, create a new Material extension with initializer:

```
private extension Material {
  init(material: MDLMaterial?) {
    self.init()
    if let baseColor = material?.property(with: .baseColor),
      baseColor.type == .float3 {
      self.baseColor = baseColor.float3Value
    }
    ambientOcclusion = 1
  }
}
```

In Submesh.Textures.init(material:), you pass a material to MDLMaterial.texture(type:) and load a texture, if there is one available for that property. If there’s no texture, you can use the material’s base color property. For example, if an object is solid red, you don’t have to go to the trouble of making a texture, you can just use the material’s base color of float3(1, 0, 0) to describe the color.

Currently, you’re not loading or using ambient occlusion, but the default value should be 1.0 (white).

➤ In Submesh, in init(mdlSubmesh:mtkSubmesh:) after initializing textures, initialize material:

`material = Material(material: mdlSubmesh.material)`

You’ll now send this material to the shader. This sequence of coding should be familiar to you by now.

➤ Open Common.h, and add another index to BufferIndices:

`MaterialBuffer = 14`

<a id="page-282"></a>

➤ Open Rendering.swift. In render(encoder:uniforms:params:), inside for submesh in mesh.submeshes where you call setFragmentTexture, add the following:

```
var material = submesh.material
encoder.setFragmentBytes(
  &material,
  length: MemoryLayout<Material>.stride,
  index: MaterialBuffer.index)
```

This code sends the material structure to the fragment shader. As long as your material structure stride is less than 4K bytes, then you don’t need to create and hold a special buffer.

➤ Open **Lighting.h** and remove the comments around the three PBR functions.

➤ Open **PBR.metal** and remove the comments from the start and end of the file.

These functions were commented because they refer to Material, which you only just defined.

➤ Open Fragment.metal, and add the following as a parameter of fragment\_main:

`constant Material &_material [[buffer(MaterialBuffer)]],`

You pass the model’s material properties to the fragment shader. You use \_ in front of the name, as \_material is constant, and soon you’ll need to update the structure with the texture’s base color if there is one.

➤ At the top of fragment\_main, add this so that you can override material values in the shader:

`Material material = _material;`

➤ In `fragment_main`, replace:

```
float3 baseColor = baseColorTexture.sample(
  textureSampler,
  in.uv * params.tiling).rgb;
```

With:

```
if (!is_null_texture(baseColorTexture)) {
  material.baseColor = baseColorTexture.sample(
  textureSampler,
  in.uv * params.tiling).rgb;
}
```

<a id="page-283"></a>

If the texture exists, replace the material base color with the color extracted from the texture. Otherwise, you’ve already loaded the base color in material.

➤ Still in fragment\_main, remove the normal and color definition which uses the Phong shader:

```
float3 normalDirection = normalize(in.worldNormal);
float3 color = phongLighting(
  normal,
  in.worldPosition,
  params,
  lights,
  baseColor
);
return float4(color, 1);
```

➤ In its place, add the following code to use the PBR shader:

```
// 1
float3 normal = normalize(in.worldNormal);
float3 diffuseColor = computeDiffuse(
  lights, params, material, normal);
// 2
float3 specularColor = computeSpecular(
  lights, params, material, normal, in.worldPosition);
// 3
float3 ambientColor = computeAmbient(
  lights, params, material);
// 4
return float4(diffuseColor + specularColor + ambientColor, 1);
```

Going through the code:

1. You first calculate the diffuse color using the lights, the material and the surface normal.

2. You then calculate the specular color, which includes using the camera position supplied in params. Compare the code in PBR.metal with the Phong shader in Lighting.metal. The PBR code has a few more elements to calculate.

3. Calculate the ambient color. The scene’s ambient lights are a very simple global illumination solution, which is absolutely unrealistic. It’s a temporary solution, until you provide more correct illumination in Chapter 21, “Image-Based Lighting”.

4. Combine the diffuse, specular and ambient colors for the final result.

<a id="page-284"></a>

➤ Build and run the app. As yet, except for one tiny white dot to the left of center, you shouldn’t see much difference. This tiny white dot is the specular highlight.

![Figure](Metal_by_Tutorials_v500mpdf/644d44cb8eee588c902a5678.png)

_PBR shading_

## **Surface Roughness**

The smoother a surface is, the shinier it should be. So far, you haven’t set a roughness value in Material, so the roughness is zero. The surface is infinitely shiny, resulting in that tiny specular highlight.

➤ In Fragment.metal, at the top of fragment\_main, after initializing material, add this:

`material.roughness = 0.35;`

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/44e4de1860220277cec6449b.png)

_Specular highlight_

<a id="page-285"></a>

The specular highlight is more noticeable now. Having a higher roughness value spreads out the specular.

Applying one roughness value to the entirety of a surface isn’t very realistic. Setting a roughness texture map will allow the fragment shader to shade each fragment differently. Your model’s roughness texture will make the bricks shiny, as if they’ve had rain on them, and the inset cement filling to be not at all shiny.

This is the sphere’s roughness texture:

![Figure](Metal_by_Tutorials_v500mpdf/2a65aa66d7b3adcb93088670.png)

_Roughness texture_

When you read in the grayscale texture, the bricks’ roughness value will be close to zero, whereas the cement will be 1.0, so will not reflect the light.

➤ Remove material.roughness = 0.35.

➤ Open Submesh.swift, and create a new property for roughness in Submesh.Textures:

`var roughness: MTLTexture?`

➤ In the Submesh.Textures extension, add the following code to the end of init(material:):

`roughness = material?.texture(type: .roughness)`

This loads the roughness texture in the same way as you loaded the color texture. In case there is no texture, you need to read in the material value too.

<a id="page-286"></a>

➤ At the bottom of Material’s init(material:), add:

```
if let roughness = material?.property(with: .roughness),
  roughness.type == .float {
  self.roughness = roughness.floatValue
}
```

Open Common.h and add the new texture index definitions to TextureIndices:

```
NormalTexture = 1,
RoughnessTexture = 2,
MetallicTexture = 3,
AOTexture = 4
```

You’re not quite ready to add the other textures yet, but you can set up the indices for later.

➤ Open Rendering.swift, and in render(encoder:uniforms:params:), locate where you send the base color texture to the fragment function, then add this code afterward:

```
encoder.setFragmentTexture(
  submesh.textures.roughness,
  index: RoughnessTexture.index)
```

You create the command to send the roughness texture to the GPU.

➤ Open Fragment.metal, and in fragment\_main, add the roughness texture to the list of parameters:

`texture2d<float> roughnessTexture [[texture(RoughnessTexture)]]`

➤ In the body of `fragment_main`, before initializing `normal`, add this:

```
if (!is_null_texture(roughnessTexture)) {
  material.roughness = roughnessTexture.sample(
    textureSampler,
    in.uv * params.tiling).r;
}
```

You read in the roughness value from the roughness texture, if there is one. If there isn’t a texture, the PBR shader will use material‘s roughness value. Unlike baseColor, roughness is a float, so you read in the value from the texture’s red channel.

<a id="page-287"></a>

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/8cb505b62d43f0fee27b4dec.png)

_Roughness texture applied_

As you rotate the scene by dragging, you’ll notice that the bricks pick up the highlight, but the cement mortar doesn’t.

The sphere is looking a bit more lively, but there’s still some detail missing. That’s where normal maps come in.

## **Normal Maps**

This is your desired final render:

![Figure](Metal_by_Tutorials_v500mpdf/76ec4fb836ffcf9ac440770a.png)

_An object rendered with a normal map_

<a id="page-288"></a>

The difference from your current render is simply that this sphere is rendered with the normal map applied. This normal map makes it appear as if the sphere is a high-poly model with lots of nooks and crannies. In truth, these high-end details are just an illusion.

The normal map texture looks like this:

![Figure](Metal_by_Tutorials_v500mpdf/a2aea49657dcfe7fe3779fef.png)

_A normal map texture_

All models have normals that stick out perpendicular to each face. For example, a cube has six faces, and the normal for each face points in a different direction. Also, each face is flat. If you wanted to create the illusion of bumpiness, you’d need to change a normal in the fragment shader.

Look at the following image. On the left is a flat surface with normals in the fragment shader. On the right, you see perturbed normals. The texels in a normal map supply the direction vectors of these normals through the RGB channels.

![Figure](Metal_by_Tutorials_v500mpdf/88cba497c2b86577a2197d1f.png)

_Normals_

Now, look at this single brick split out into the red, green and blue channels that make up an RGB image.

<a id="page-289"></a>

![Figure](Metal_by_Tutorials_v500mpdf/55ce3fc68a9bac72c45adcb2.png)

_Normal map channels_

Each channel has a value between 0 and 1, and you generally visualize them in grayscale as it’s easier to read color values. For example, in the red channel, a value of 0 is no red at all, while a value of 1 is full red. When you convert 0 to an RGB color (0, 0, 0), the result is black. On the opposite spectrum, (1, 1, 1) is white. And in the middle, you have (0.5, 0.5, 0.5), which is mid-gray. In grayscale, all three RGB values are the same, so you only need to refer to a grayscale value by a single float.

Take a closer look at the edges of the red channel’s brick. Look at the left and right edges in the grayscale image. The red channel has the darkest color where the normal values of that fragment should point left (-X, 0, 0), and the lightest color where they should point right (+X, 0, 0).

Now look at the green channel. The left and right edges have equal value but are different for the top and bottom edges of the brick. The green channel in the grayscale image has darkest for pointing down (0, -Y, 0) and lightest for pointing up (0, +Y, 0).

Finally, the blue channel is mostly white in the grayscale image because the brick — except for a few irregularities in the texture — points outward. The edges of the brick are the only places where the normals should point away.

Note: Normal maps can be either right-handed or left-handed. Your renderer will expect positive y to be up, but some apps will generate normal maps with positive y down. To fix this, you can take the normal map into Photoshop and invert the green channel.

<a id="page-290"></a>

The base color of a normal map — where all normals are “normal” (orthogonal to the face) — is (0.5, 0.5, 1).

![Figure](Metal_by_Tutorials_v500mpdf/bf7d3491681fe7cdebdc9532.png)

_A flat normal map_

This is an attractive color but was not chosen arbitrarily. RGB colors have values between 0 and 1, whereas a model’s normal values are between -1 and 1. A color value of 0.5 in a normal map translates to a model normal of 0. The result of reading a flat texel from a normal map should be a z value of 1 and the x and y values as 0. Converting these values (0, 0, 1) into the colorspace of a normal map results in the color (0.5, 0.5, 1). This is why most normal maps appear bluish.

Looking at normal map textures in a photo editor, you’d think they are color, but the trick is to regard the RGB values as numerical data instead of color data.

Note: Most 3D models will have normal values included, but you may come across odd files where you have to generate normals. Model I/O can create normals using MDLMesh.addNormals(withAttributeNamed:creaseThreshold:). The creaseThreshold accounts for how much you want the edges of each polygon smoothed.

## **Creating Normal Maps**

To create successful normal maps, you need a specialized app. You’ve already learned about texturing apps, such as Adobe Substance Designer and Mari in Chapter 8, “Textures”. Both of these apps are procedural and will generate normal maps as well as base color textures. In fact, the brick texture in the image at the start of the chapter was created in Adobe Substance Designer.

<a id="page-291"></a>

Sculpting programs, such as ZBrush, 3D-Coat and Blender will also generate normal maps from your sculpts. You first sculpt a detailed high-poly mesh. And then the app looks at the cavities and curvatures of your sculpt and bakes a normal map. Because high-poly meshes with tons of vertices aren’t resource-efficient in games, you should create a low-poly mesh and then apply the normal map to this mesh.

Photoshop and Adobe Substance 3D Sampler can generate a normal map from a photograph or diffuse texture. Because these apps look at the shading and calculate the values, they aren’t as good as the sculpting or procedural apps, but it can be quite amazing to take a photograph of a real-life, personal object, run it through one of these apps, and render out a shaded model.

Here’s a normal map that was created using Adobe’s Bitmap2Material:

![Figure](Metal_by_Tutorials_v500mpdf/08e1b3bb9a7950bd1f082bc7.png)

_A cross photographed and converted into a normal map_

On the right, the normal map is rendered on to a simple cube model with minimal geometry and a white base color.

## **Tangent Space**

To render with a normal map texture, you send it to the fragment function in the same way as a color texture, and you extract the normal values using the same UVs. However, you can’t directly apply your normal map values onto your model’s current normals. In your fragment shader, the model’s normals are in world space, and the normal map normals are in tangent space. Tangent space is a little hard to wrap your head around. Think of a cube with all its six faces pointing in different directions. Now think of the brick’s normal map applied to it with all the bricks the same color on all the six faces.

<a id="page-292"></a>

If a cube face is pointing toward negative x, how does the normal map know to point in that direction?

![Figure](Metal_by_Tutorials_v500mpdf/c5a26dd755e7e57469310e20.png)

_Normals on a sphere_

Using a sphere as an example, every fragment has a tangent — that’s the line that touches the sphere at that point. The normal vector in this tangent space is thus relative to the surface. You can see that all of the arrows are at right angles to the tangent. So if you took all of the tangents and laid them out on a flat surface, the blue arrows would point upward in the same direction. That’s tangent space!

The following image shows a cube’s normals in world space.

![Figure](Metal_by_Tutorials_v500mpdf/c11bf906d0f870a55fb3f2f8.png)

_Visualizing normals in world space_

<a id="page-293"></a>

To convert the cube’s normals to tangent space, you create a TBN matrix - that’s a Tangent Bitangent Normal matrix that’s calculated from the tangent, bitangent and normal value for each vertex.

![Figure](Metal_by_Tutorials_v500mpdf/2ffdcbd1e0e692392b6e6dd6.png)

_The TBN matrix_

In the TBN matrix, the normal is the perpendicular vector as usual; the tangent is the vector that points along the horizontal surface; and the bitangent is the vector — as calculated by the cross product — that is perpendicular to both the tangent and the normal.

Note: The cross product is an operation that gives you a vector perpendicular to two other vectors.

The tangent can be at right angles to the normal in any direction. However, to share normal maps across different parts of models, and even entirely different models, there are two standards:

1. The tangent and bitangent will represent the directions that u and v point, respectively, defined in model space.

2. The red channel will represent curvature along u, and the green channel, along v.

You could calculate these values when you load the model. However, with Model I/O, as long as you have data for both the position and texture coordinate attributes, Model I/O can calculate and store these tangent and bitangent values at each vertex for you.

<a id="page-294"></a>

## **Using Normal Maps**

➤ In the Geometry folder, open Submesh.swift, and add a new property to Submesh.Textures:

`var normal: MTLTexture?`

➤ At the end of `SubMesh.Textures.init(material:)`, read in this texture:

`normal = material?.texture(type: .tangentSpaceNormal)`

You read in the normal map texture that the submesh points to.

➤ Open Rendering.swift, and in render(encoder:uniforms:params:), locate where you set the base color texture inside for submesh in mesh.submeshes.

➤ Add this:

```
encoder.setFragmentTexture(
  submesh.textures.normal,
  index: NormalTexture.index)
```

Here, you send the normal texture to the GPU.

➤ Open Fragment.metal, and in fragment\_main, add the normal texture to the list of parameters:

`texture2d<float> normalTexture [[texture(NormalTexture)]]`

Now that you’re transferring the normal texture map, the first step is to apply it to the sphere as if it were a color texture.

➤ In fragment\_main, replace float3 normal = normalize(in.worldNormal); with this:

```
float3 normal;
if (is_null_texture(normalTexture)) {
  normal = in.worldNormal;
} else {
  normal = normalTexture.sample(
  textureSampler,
  in.uv * params.tiling).rgb;
}
normal = normalize(normal);
return float4(normal, 1);
```

<a id="page-295"></a>

Since not all models will come complete with textures, you check whether a texture is present. You read in the normal value from the texture, if there is one, otherwise set the default normal value. The return is only temporary to make sure the app is loading the normal map correctly, and that the normal map and UVs match.

➤ Build and run to verify the normal map is providing the fragment color.

![Figure](Metal_by_Tutorials_v500mpdf/2c2af224a0fc87d27c5dc810.png)

_The normal map applied as a color texture_

You can see all the surface details the normal map will provide.

Note: the render looks a little pale because the normal map is (correctly) read in as data rather than sRGB color, and then rendered in the view’s sRGB color space.

➤ Excellent! You tested that the normal map loads, so remove this from fragment\_main:

`return float4(normal, 1);`

Don’t celebrate just yet. You still have several tasks ahead of you. If you ran the app now, you’d get some weird lighting and no color. You still need to:

1. Load tangent and bitangent values using Model I/O.

2. Tell the render command encoder to send the newly created MTLBuffers containing the values to the GPU.

<a id="page-296"></a>

3. In the vertex shader, change the tangent and bitangent values to world space — just as you did normals — and pass the new values to the fragment shader.

4. Calculate the new normal based on these values.

## **1. Load Tangents and Bitangents**

Model I/O will create tangent and bitangent attributes for you in new MTLBuffers. First, define these new buffer attribute and buffer indices.

➤ Open Common.h and add this to Attributes:

```
Tangent = 3,
Bitangent = 4
```

➤ Add the indices to BufferIndices:

```
TangentBuffer = 2,
BitangentBuffer = 3,
```

➤ Open VertexDescriptor.swift, and look at MDLVertexDescriptor’s defaultLayout.

Here, you tell the vertex descriptor that there are position, normal and UV attributes. Model I/O will create the tangent and bitangent attribute values in buffers, but you have to tell the GPU to read in these buffers.

When you create the pipeline state in Renderer, the pipeline descriptor uses defaultLayout as the vertex descriptor, and will now notify the GPU that it needs to create space for these two extra buffers. It’s important that you remember that your model’s vertex descriptor layout must match the one in the render encoder’s pipeline state.

➤ Add this to MDLVertexDescriptor’s defaultLayout before return:

```
vertexDescriptor.attributes[Tangent.index] =
  MDLVertexAttribute(
    name: MDLVertexAttributeTangent,
    format: .float3,
    offset: 0,
    bufferIndex: TangentBuffer.index)
vertexDescriptor.layouts[TangentBuffer.index]
  = MDLVertexBufferLayout(stride: MemoryLayout<float3>.stride)
vertexDescriptor.attributes[Bitangent.index] =
  MDLVertexAttribute(
    name: MDLVertexAttributeBitangent,
```

<a id="page-297"></a>

```
    format: .float3,
    offset: 0,
    bufferIndex: BitangentBuffer.index)
vertexDescriptor.layouts[BitangentBuffer.index]
  = MDLVertexBufferLayout(stride: MemoryLayout<float3>.stride)
```

You set up definitions and indices for two buffers, one for tangents and one for bitangents.

Note: So far, you’ve only created one pipeline descriptor for all models. But often models will require different vertex layouts. Or if some of your models don’t contain normals, colors and tangents, you might wish to save on creating buffers for them. You can create multiple pipeline states for the different vertex descriptor layouts, and replace the render encoder’s pipeline state before drawing each model.

➤ Open **Model.swift** in the **Geometry** folder, and in `init(name:)`, replace:

```
let (mdlMeshes, mtkMeshes) = try! MTKMesh.newMeshes(
  asset: asset,
  device: Renderer.device)
```

With:

```
var mtkMeshes: [MTKMesh] = []
let mdlMeshes =
  asset.childObjects(of: MDLMesh.self) as? [MDLMesh] ?? []
_ = mdlMeshes.map { mdlMesh in
  mtkMeshes.append(
    try! MTKMesh(
      mesh: mdlMesh,
      device: Renderer.device))
}
```

Because you need to change the mesh with tangents and bitangents, you extract all the MDLMeshes from the asset. You create an MTKMesh array from these MDLMeshes.

<a id="page-298"></a>

➤ Before `mtkMeshes.append`, add this code:

```
mdlMesh.addTangentBasis(
  forTextureCoordinateAttributeNamed:
    MDLVertexAttributeTextureCoordinate,
  tangentAttributeNamed: MDLVertexAttributeTangent,
  bitangentAttributeNamed: MDLVertexAttributeBitangent)
```

For each `MDLMesh`, add the tangent and bitangent values.

Model I/O does a few things behind the scenes:

• Add two named attributes to mdlMesh’s vertex descriptor: MDLVertexAttributeTangent and MDLVertexAttributeBitangent.

• Calculate the tangent and bitangent values.

• Create two new MTLBuffers to contain them.

• Update the layout strides on mdlMesh’s vertex descriptor to match the two new buffers.

Your default vertex descriptor matches the one set up by Model I/O.

## 2. Send Tangent and Bitangent Values to the GPU

➤ Open Rendering.swift, and in render(encoder:uniforms:params:), locate for mesh in meshes.

For each mesh, you’re currently sending all the vertex buffers to the GPU:

```
for (index, vertexBuffer) in mesh.vertexBuffers.enumerated() {
  encoder.setVertexBuffer(
    vertexBuffer,
    offset: 0,
    index: index)
}
```

This code includes sending the tangent and bitangent buffers. You should be aware of the number of buffers that you send to the GPU. In Common.h, you’ve set up UniformsBuffer as index 11, but if you had defined that as index 3, you’d now have a conflict with the bitangent buffer.

<a id="page-299"></a>

➤ Build and run the app to make sure your sphere still renders. Drag the sphere around to check whether the specular lighting works.

![Figure](Metal_by_Tutorials_v500mpdf/317d5c23d6e4b31b185451c9.png)

_Normal calculations are wrong_

That’s disappointing. All this work and you appear to have taken a step backward. But don’t worry! In computer graphics, when you apply the right calculations in the shader, your render can often resolve into glorious technicolor .

## 3. Convert Tangent and Bitangent Values to World Space

Just as you converted the model’s normals to world space, you need to convert the tangents and bitangents to world space in the vertex function.

➤ In the Shaders folder, open ShaderDefs.h, and add these new attributes to VertexIn:

```
float3 tangent [[attribute(Tangent)]];
float3 bitangent [[attribute(Bitangent)]];
```

<a id="page-300"></a>

➤ Add new properties to VertexOut so that you can send the values to the fragment function:

```
float3 worldTangent;
float3 worldBitangent;
```

➤ Open Vertex.metal and in vertex\_main after calculating out.worldNormal, add this:

```
.worldTangent = uniforms.normalMatrix * in.tangent,
.worldBitangent = uniforms.normalMatrix * in.bitangent
```

This code moves the tangent and bitangent values into world space.

## **4. Calculate the New Normal**

Now that you have everything in place, it’ll be a simple matter to calculate the new normal.

Before doing the normal calculation, consider the normal color value that you’re reading. Colors are between 0 and 1, but normal values range from -1 to 1.

➤ Open Fragment.metal and in fragment\_main, locate where you sample normalTexture. In the else part of the conditional, after reading the normal from the texture, add:

`normal = normal * 2 - 1;`

This code redistributes the normal value to be within the range -1 to 1.

➤ After the previous code, still inside the `else` part of the conditional, add this:

```
normal = float3x3(
  in.worldTangent,
  in.worldBitangent,
  in.worldNormal) * normal;
```

This code recalculates the normal direction into tangent space to match the tangent space of the normal texture.

<a id="page-301"></a>

➤ Build and run the app to see the normal map applied to the sphere.

![Figure](Metal_by_Tutorials_v500mpdf/76ec4fb836ffcf9ac440770a.png)

_The sphere with a normal map applied_

What a difference! As you rotate the scene, notice how the lighting affects the small cavities on the model — it’s almost like you created new geometry, but you didn’t. That’s the magic of normal maps: Adding amazing detail to simple low-poly models.

## **Other Texture Map Types**

Normal and roughness maps are not the only way of changing a model’s surface. You can replace material values with any texture. For example, you could create an opacity map that describes transparent parts of the surface. Or a reflection map that builds in reflected objects.

In fact, any value (thickness, curvature, etc.) that you can think of to describe a surface, can be stored in a texture. You just look up the relevant fragment in the texture using the UV coordinates and use the value recovered. That’s one of the bonuses of writing your own renderer. You can choose what maps to use and how to apply them.

You use all of these textures in the fragment shader, and the geometry doesn’t change.

Note: A displacement or height map can change geometry. You’ll read about displacement in Chapter 19, “Tessellation &amp; Terrains”.

<a id="page-302"></a>

## **Challenge**

Your challenge is to download and render the toy drummer model from Apple’s AR Quick Look gallery (https://developer.apple.com/augmented-reality/quick-look/).

In **GameScene.swift**, you’ll need to change:

• defaultView: Change the rotation to [-0.1, 9.8, 0.0]

• init(): Change the camera distance to 14 and the target to [0, 7, 0].

This will position the drummer center stage.

Change SceneLighting to match the challenge project’s lighting. There is an additional light to fully show off the drummer.

Your first render should look like this:

![Figure](Metal_by_Tutorials_v500mpdf/da34254403db3d616502100c.png)

_Rendering a toy drummer_

After your first render, just as you did with the roughness texture, add metallic and ambient occlusion textures to your code in Submesh, Rendering.swift and fragment\_main. Then, admire your final physically-based render. The drumsticks are metallic, and the shadowing under the drummer’s chin comes from the ambient occlusion map.

<a id="page-303"></a>

![Figure](Metal_by_Tutorials_v500mpdf/a1c95617c9d8a2bdebf6349c.png)

_The final render_

## **Where to Go From Here?**

Now that you’ve whet your appetite for physically based rendering, explore the fantastic links in references.markdown, which you’ll find in the resources folder for this chapter. Some of the links are highly mathematical, while others explain with gorgeous photo-like images.

<a id="page-304"></a>

# 12

# Chapter 12: Render Passes

Up to this point, you’ve created projects that had only one render pass. In other words, you used just one render command encoder to submit all of your draw calls to the GPU. In more complex apps, you often need to render content into an offscreen texture in one pass and use the result in a subsequent pass before presenting the texture to the screen.

There are several reasons why you might do multiple passes:

• Shadows: In the following chapter, you’ll create a shadow pass and render a depth map from a directional light to help calculate shadows in a subsequent pass.

• Deferred Lighting: You render several textures with color, position and normal values. Then, in a final pass, you calculate lighting using those textures.

• Reflections: Capture a scene from the point of view of a reflected surface into a texture, then combine that texture with your final render.

• Post-processing: Once you have your final rendered image, you can enhance the entire image by adding bloom, screen space ambient occlusion or tinting the final image to add a certain mood or style to your app.

<a id="page-305"></a>

## **Render Passes**

A render pass consists of sending commands to a command encoder. The pass ends when you end encoding on that command encoder.

When setting up a render command encoder, you use a render pass descriptor. So far, you’ve used MTKView.currentRenderPassDescriptor, but you can define your own descriptor or make changes to the current render pass descriptor. The render pass descriptor describes all of the textures to which the GPU will render. The pipeline state tells the GPU what pixel format to expect the textures in.

![Figure](Metal_by_Tutorials_v500mpdf/7062b7635fc893a2c7c2d6a8.png)

_A render pass_

<a id="page-306"></a>

For example, the following render pass writes to four render target textures. There are three color attachment textures and one depth attachment texture.

![Figure](Metal_by_Tutorials_v500mpdf/321db5869a2b20bb017bbbbf.png)

_A render pass with four textures_

<a id="page-307"></a>

## **Object Picking**

To get started with multipass rendering, you’ll create a simple render pass that adds object picking to your app. When you click a model in your scene, that model will render in a slightly different shade.

There are several ways to hit-test rendered objects. For example, you could do the math to convert the 2D touch location to a 3D ray and then perform ray intersection to see which object intersects the ray. Warren Moore describes this method in his Picking and Hit-Testing in Metal (https://is.gd/iBVDO8) article. Alternatively, you could render a texture where each object is rendered in a different color or object ID. Then, you calculate the texture coordinate from the screen touch location and read the texture to see which object was hit.

You’re going to store the model’s object ID into a texture in one render pass. You’ll then send the touch location to the fragment shader in the second render pass and read the texture from the first pass. If the fragment being rendered is from the selected object, you’ll render that fragment in a different color.

## **The Starter App**

➤ In Xcode, open the starter app for this chapter and examine the code. It’s similar to the previous chapter but refactored.

• In the Render Passes folder, ForwardRenderPass.swift contains the rendering code that used to be in Renderer along with the pipeline state and depth stencil state initialization. Separating this code will make it easier to have multiple render passes because you can then concentrate on getting the pipeline states and textures correct for each pass. In Renderer, draw(scene:in:) updates the uniforms, then tells the forward render pass to draw the scene.

• Pipelines.swift contains pipeline state creation. Later, PipelineStates will contain several more pipeline states.

• In the Game folder, GameScene sets up new models in a scene.

• In the Geometry folder, Model now has an objectId. When GameScene creates the model, in createModel(name:), it allocates a unique object ID. Model.render(encoder:uniforms:params:) updates params with its objectId for the fragment function. The ground has an object ID of zero.

<a id="page-308"></a>

• In the Shaders folder, Common.h has some extra properties in Params to pass a touch location to the fragment function. Renderer initializes the scale factor of the device in params. Most retina devices have a scale factor of 2, however, iPhone Pro Max has a scale factor of 3.

➤ Build and run the app, and familiarize yourself with the code.

![Figure](Metal_by_Tutorials_v500mpdf/e952345feeb70a170b1bd078.png)

_The starter app_

## **Setting up Render Passes**

Since you’ll have multiple render passes performing similar procedures, it makes sense to have a protocol with some default methods.

➤ In the Renderer folder, create a new Swift file named RenderPass.swift, and replace the code with:

```
import MetalKit

protocol RenderPass {
  var label: String { get }
  var descriptor: MTLRenderPassDescriptor? { get set }
  mutating func resize(view: MTKView, size: CGSize)
  func draw(
    commandBuffer: MTLCommandBuffer,
    scene: GameScene,
    uniforms: Uniforms,
    params: Params
  )
}
```

<a id="page-309"></a>

```
extension RenderPass {
}
```

All render passes will have a render pass descriptor. The pass might create its own descriptor or use the view’s current render pass descriptor. They’ll all need to resize the render textures when the user resizes the window. All render passes will need a draw method.

The extension will hold default render pass methods.

➤ Open ForwardRenderPass.swift, and conform ForwardRenderPass to RenderPass:

`struct ForwardRenderPass: RenderPass {`

➤ Cut buildDepthStencilState() from ForwardRenderPass, and paste it into RenderPass’s extension.

Multiple render passes will use this depth stencil state initialization method.

## **Creating a UInt32 Texture**

Textures don’t only hold color. There are many pixel formats (https://apple.co/ 3Eby9oD). Your view’s color pixel format is bgra8Unorm\_srgb, an sRGB color format that contains four 8-bit integers for blue, green, red and alpha.

Model‘s objectId is a UInt32, and instead of the model’s color, you’ll render the object ID to a texture. You’ll create a texture that holds UInt32s in a new render pass.

➤ In the Render Passes folder, create a new Swift file named ObjectIdRenderPass.swift and replace the code with:

```
import MetalKit

struct ObjectIdRenderPass: RenderPass {
  let label = "Object ID Render Pass"
  var descriptor: MTLRenderPassDescriptor?
  var pipelineState: MTLRenderPipelineState

  mutating func resize(view: MTKView, size: CGSize) {
  }

  func draw(
    commandBuffer: MTLCommandBuffer,
```

<a id="page-310"></a>

```
    scene: GameScene,
    uniforms: Uniforms,
    params: Params
  ) {
  }
}
```

Here, you create the render pass with the required properties and methods to conform to RenderPass, along with a pipeline state object.

➤ Open Pipelines.swift, and add a method to PipelineStates to create the pipeline state object:

```
static func createObjectIdPSO() -> MTLRenderPipelineState {
  let pipelineDescriptor = MTLRenderPipelineDescriptor()
  // 1
  let vertexFunction =
    Renderer.library?.makeFunction(name: "vertex_main")
  let fragmentFunction =
    Renderer.library?.makeFunction(name: "fragment_objectId")
  pipelineDescriptor.vertexFunction = vertexFunction
  pipelineDescriptor.fragmentFunction = fragmentFunction
  // 2
  pipelineDescriptor.colorAttachments[0].pixelFormat = .r32Uint
  // 3
  pipelineDescriptor.depthAttachmentPixelFormat = .invalid
  pipelineDescriptor.vertexDescriptor =
    MTLVertexDescriptor.defaultLayout
  return Self.createPSO(descriptor: pipelineDescriptor)
}
```

Most of this code will be familiar to you, but there are some details to note:

1. You can use the same vertex function as you did to render the model because you’ll render the vertices in the same position. However, you’ll need a different fragment function to write the ID to the texture.

2. The color attachment’s texture pixel format is a 32-bit unsigned integer. The GPU will expect you to hand it a texture in this format.

3. You’ll come back and add a depth attachment, but for now, leave it invalid, which means that the GPU won’t require a depth texture.

<a id="page-311"></a>

➤ Open **ObjectIdRenderPass.swift**, and create an initializer:

```
init() {
  pipelineState = PipelineStates.createObjectIdPSO()
  descriptor = MTLRenderPassDescriptor()
}
```

Here, you initialize the pipeline state and the render pass descriptor.

Most render passes will require you to create a texture, so you’ll create one that takes several different parameters.

➤ Open **RenderPass.swift**, and add a new method to the extension:

```
static func makeTexture(
  size: CGSize,
  pixelFormat: MTLPixelFormat,
  label: String,
  storageMode: MTLStorageMode = .private,
  usage: MTLTextureUsage = [.shaderRead, .renderTarget]
) -> MTLTexture? {
}
```

In addition to a size, you’ll give the texture:

• A pixel format, such as rgba8Unorm. In this render pass, you give it r32Uint.

• By default, the storage mode is private, meaning the texture stores in memory in a place that only the GPU can access.

• The usage. You have to configure textures used by render pass descriptors as render targets. Render targets are memory buffers or textures that allow offscreen rendering for cases where the rendered pixels don’t need to end up in the framebuffer. You’ll also want to read the texture in shader functions, so you set up that default capability, too.

➤ Add this code to makeTexture(size:pixelFormat:label:storageMode:usage:):

```
let width = Int(size.width)
let height = Int(size.height)
guard width > 0 && height > 0 else { return nil }
let textureDesc =
  MTLTextureDescriptor.texture2DDescriptor(
    pixelFormat: pixelFormat,
    width: width,
    height: height,
    mipmapped: false)
```

<a id="page-312"></a>

```
textureDesc.storageMode = storageMode
textureDesc.usage = usage
guard let texture =
  Renderer.device.makeTexture(descriptor: textureDesc) else {
    fatalError("Failed to create texture")
  }
texture.label = label
return texture
```

You configure a texture descriptor using the given parameters and create a texture from the descriptor.

➤ Open ObjectIdRenderPass.swift, and add a new property to ObjectIdRenderPass for the render texture:

`var idTexture: MTLTexture?`

➤ Add this code to resize(view:size:):

```
idTexture = Self.makeTexture(
  size: size,
  pixelFormat: .r32Uint,
  label: "ID Texture")
```

Every time the view size changes, you’ll rebuild the texture to match the view’s size.

Now for the draw.

➤ Add this code to draw(commandBuffer:scene:uniforms:params:):

```
guard let descriptor = descriptor else {
  return
}
descriptor.colorAttachments[0].texture = idTexture
guard let renderEncoder =
  commandBuffer.makeRenderCommandEncoder(descriptor: descriptor)
else { return }
```

The descriptor will be the view’s default render pass descriptor, passed in by Renderer. The default render pass descriptor’s first color attachment is the view’s drawable. You override this with idTexture. You then create the render command encoder using this descriptor. The render target texture’s pixel format must match the pipeline state object’s pixel format for color attachment zero. In this case, you set them both to r32Uint.

<a id="page-313"></a>

➤ Add this code after the code you just added:

```
renderEncoder.label = label
renderEncoder.setRenderPipelineState(pipelineState)
for model in scene.models {
  model.render(
    encoder: renderEncoder,
    uniforms: uniforms,
    params: params)
}
renderEncoder.endEncoding()
```

Here, you set the pipeline state and render the models.

## **Adding the Render Pass to Renderer**

➤ Open **Renderer.swift**, and add the new render pass property:

`var objectIdRenderPass: ObjectIdRenderPass`

➤ In init(metalView:options:), add this code before super.init() to initialize the render pass:

`objectIdRenderPass = ObjectIdRenderPass()`

➤ Add this code to mtkView(\_:drawableSizeWillChange:):

`objectIdRenderPass.resize(view: view, size: size)`

Here, you ensure that idTexture’s size matches the view size. Renderer’s initializer calls mtkView(\_:drawableSizeWillChange), so your texture in the render pass is initialized and sized appropriately.

➤ Add this code to draw(scene:in:) immediately after // Draw scene, before starting the forward render pass:

```
objectIdRenderPass.draw(
  commandBuffer: commandBuffer,
  scene: scene,
  uniforms: uniforms,
  params: params)
```

Excellent, you’ve set up the render pass. Now all you have to do is create the fragment shader function to write to idTexture.

<a id="page-314"></a>

## **Adding the Shader Function**

The Object ID render pass will write the currently rendered model’s object ID to a texture. You don’t need any of the vertex information in the fragment function.

➤ In **Shaders**, create a new Metal File named **ObjectId.metal** and add:

```
#import "Common.h"

// 1
struct FragmentOut {
  uint objectId [[color(0)]];
};

// 2
fragment FragmentOut fragment_objectId(
  constant Params &params [[buffer(ParamsBuffer)]])
{
  // 3
  FragmentOut out {
    .objectId = params.objectId
  };
  return out;
}
```

Going through this code:

1. You create a structure that matches the render pass descriptor color attachment. Color attachment 0 contains the object ID texture.

2. The fragment function takes in params, of which you only need the object ID.

3. You create a FragmentOut instance and write the current object ID to it. You then return it from the fragment function, and the GPU writes the fragment into the given texture.

<a id="page-315"></a>

➤ Build and run the app.

You won’t see a difference in your render. Currently, you’re not passing on the object ID texture to the second render pass.

![Figure](Metal_by_Tutorials_v500mpdf/4f3c7445f3c1e56bd4eb75f3.png)

_No difference to the render_

➤ Capture the GPU workload by clicking the Metal icon and clicking Capture in the popup.

![Figure](Metal_by_Tutorials_v500mpdf/687915b2c2456fc2b1c5f207.png)

_The Capture GPU workload icon_

<a id="page-316"></a>

➤ Click the command buffer, and you’ll see two render passes. The Object ID render pass is on the left with an R32Uint pixel format texture. The usual forward render pass is at the top right and has a color texture and a depth texture.

![Figure](Metal_by_Tutorials_v500mpdf/8a9f7b1d753c318c476b5915.png)

_The GPU workload capture_

The green Present is the Metal drawable texture that’s presented to the screen. The Object ID Render Pass isn’t passing any information to Present.

<a id="page-317"></a>

➤ Double-click the Object ID Render Pass texture twice and click on the displayed Color 0 attachment. This is idTexture.

As you move your cursor over the pixels, it shows you the value of that pixel. In your fragment function, you set the fragment to show the object ID, but almost all of the texture shows an object ID of zero. The ground, which has an object ID of zero, is rendering on top of all the other objects.

![Figure](Metal_by_Tutorials_v500mpdf/7800d53554b0fd186efbb909.png)

_ID texture with erroneous object ID_

Note: Your texture may show less red. Currently, the texture isn’t cleared at the start of the render pass, so any of the texture that wasn’t set in the fragment shader may contain any value.

To get the correct object ID, it’s important to discard models’ fragments that are behind other models. For this reason, you’ll need to render with a depth texture.

## **Adding the Depth Attachment**

➤ Open ObjectIdRenderPass.swift, and add a new property to ObjectIdRenderPass:

`var depthTexture: MTLTexture?`

So far, you’ve used the current drawable’s default depth texture. Next, you’ll create a depth texture that you’ll maintain.

<a id="page-318"></a>

➤ Add this code to resize(view:size):

```
depthTexture = Self.makeTexture(
  size: size,
  pixelFormat: Renderer.viewDepthPixelFormat,
  label: "ID Depth Texture")
```

Here, you create the depth texture with the correct size and pixel format that you set up in Renderer. This pixel format must match the render pipeline state depth texture format.

➤ Open Pipelines.swift, and in createObjectIdPSO(), change pipelineDescriptor.depthAttachmentPixelFormat = .invalid to:

```
pipelineDescriptor.depthAttachmentPixelFormat =
  Renderer.viewDepthPixelFormat
```

Now the pixel formats will match.

➤ Go back to ObjectIdRenderPass.swift. In draw(commandBuffer:scene:uniforms:params:), after setting the color attachment texture, add:

`descriptor.depthAttachment.texture = depthTexture`

You created and stored a depth texture. If you were to build and run now and capture the GPU workload, you’d see the depth texture, but you haven’t completed setting up the GPU’s depth rendering yet.

## **The Depth Stencil State**

➤ Create a new property in ObjectIdRenderPass:

`var depthStencilState: MTLDepthStencilState?`

➤ Add this code to the end of init():

`depthStencilState = Self.buildDepthStencilState()`

You set up a depth stencil state object with the usual depth rendering.

<a id="page-319"></a>

➤ In draw(commandBuffer:scene:uniforms:params:), add the following code after setting the render pipeline state:

`renderEncoder.setDepthStencilState(depthStencilState)`

Here, you let the GPU know about the depth setting you want to render with.

➤ Build and run the app. Capture the GPU workload and take a look at your Object ID color texture now.

Your texture may appear dark. This is because the Debugger is showing the object IDs 0 to 4 as a color. White will be the largest possible value, which is 4,292,442,372. So 4 will be almost black. You can remap the colors using the icon at the top left of the view.

![Figure](Metal_by_Tutorials_v500mpdf/62468a9bbef9c9ff1ffe6710.png)

_ID texture with Object IDs_

Now when you run the magnifier over each object, you’ll clearly see the object IDs.

You may see some random pixels at the top of the render. When you load the texture, the render pass executes a load action. The current load action for the texture is dontCare, so wherever you’re not rendering an object, the pixels will be random.

<a id="page-320"></a>

You’ll need to clear the texture before you render to know exactly what object ID is in the area you click to select.

![Figure](Metal_by_Tutorials_v500mpdf/86fa5cb733499d7825a73767.png)

_Load and store actions_

Note: In reality, it doesn’t matter whether you clear on load in this example. As you’ll see shortly, the change of color of each fragment on a picked object will only occur during the fragment function. Since the non-rendered pixels at the top of the screen aren’t being processed through a fragment function, a change of color will never happen. However, it’s good practice to know what’s happening in your textures. At some point, you might decide to pass back the texture to the CPU for further processing.

## **Load & Store Actions**

A render pass executes the load action whenever it loads an attachment texture before writing to it. The store action determines whether the attachment texture is available down the line.

You set up load and store actions in the render pass descriptor attachments.

➤ Open ObjectIdRenderPass.swift. In draw(commandBuffer:scene:uniforms:params:), after setting descriptor.colorAttachments[0].texture, add:

```
descriptor.colorAttachments[0].loadAction = .clear
descriptor.colorAttachments[0].storeAction = .store
```

<a id="page-321"></a>

The load action can be clear, load or dontCare. The most common store actions are store or dontCare.

Only clear the texture if you need to. If your fragment function writes to every fragment that appears on-screen, you generally don’t need to clear. For example, you don’t need to clear if you render a full-screen quad.

➤ Build and run the app, and capture the GPU workload again. Recheck the object ID texture.

![Figure](Metal_by_Tutorials_v500mpdf/2eb1416a3b2d374f8b7cbe43.png)

_No random pixels_

The pixels at the top of the screen are now cleared with zeros. If you want a non-zero clear value, set colorAttachments[0].clearColor.

## **Reading the Object ID Texture**

You now have a choice. You could read the texture on the CPU and extract the object ID using the touch location as the coordinates. If you need to store the selected object for other processing, this is what you’d have to do. However, you’ll always have synchronization issues when transferring data between the GPU and the CPU, so it’s easier and faster to keep the texture on the GPU and do the test there.

➤ Open ForwardRenderPass.swift, and add this new property to ForwardRenderPass:

`weak var idTexture: MTLTexture?`

`idTexture` will hold the ID texture from the object ID render pass.

<a id="page-322"></a>

➤ Open Renderer.swift. In draw(scene:in:), add this code after objectIdRenderPass.draw(...):

`forwardRenderPass.idTexture = objectIdRenderPass.idTexture`

You pass the ID texture from one render pass to the next.

➤ Open ForwardRenderPass.swift. In draw(commandBuffer:scene:uniforms:params:), before the for render loop, add:

`renderEncoder.setFragmentTexture(idTexture, index: 11)`

You pass idTexture to the forward render pass’s fragment function. Be careful with your index numbers. You may want to rename this one as you did with earlier indices.

You’ll also need to send the touch location to the fragment shader so you can use it to read the ID texture.

➤ After the previous code, add:

```
let input = InputController.shared
var params = params
params.touchX = UInt32(input.touchLocation?.x ?? 0)
params.touchY = UInt32(input.touchLocation?.y ?? 0)
```

input.touchLocation is the last location touched on the metal view. The SwiftUI gesture updates it in ContentView.

➤ Open Fragment.metal. and add this code to the parameters of fragment\_main:

`texture2d<uint32_t> idTexture [[texture(11)]]`

Be mindful of the type of texture you pass and the index number.

➤ After the conditional that sets `material.baseColor`, add:

```
if (!is_null_texture(idTexture)) {
  uint2 coord = uint2(
    params.touchX * params.scaleFactor,
    params.touchY * params.scaleFactor);
  uint objectID = idTexture.read(coord).r;
  if (params.objectId != 0 && objectID == params.objectId) {
    material.baseColor = float3(1.0, 0.4, 0);
  }
}
```

<a id="page-323"></a>

Here, you read idTexture using the passed-in touch coordinates. idTexture is the same size as the view’s drawable. This size is the pixel resolution of the view, and not the point size of the view.

Sometimes it’s worthwhile to halve texture sizes to save resources. You could certainly do that here, as long as you remember to halve the coordinates when reading the texture in the fragment function.

Notice that read differs from sample. read uses pixel coordinates rather than normalized coordinates. You don’t need a sampler to read a texture, but you also can’t use the various sampler options when you use read.

If the currently rendered object ID isn’t zero and the object ID matches the fragment in idTexture, change the material’s base color to orange.

➤ Build and run the app and test that your object picking works on different resolutions. iPhone Pro Max has a 3x resolution scale.

![Figure](Metal_by_Tutorials_v500mpdf/5fba565526023eb069b57840.png)

_Selected train turns orange_

The object you pick will turn orange. When you click the sky or the ground which has an object ID of zero, none of the objects are picked.

This is an easy way to test whether an object is picked. It’s also a good way to learn simple render pass texture chaining. However, in most circumstances, you’ll need to pass back the texture to the CPU, so it’s more efficient to perform ray picking as described at the beginning of the chapter.

<a id="page-324"></a>

➤ With the app running, capture the GPU workload, and click the command buffer to see the frame graph.

![Figure](Metal_by_Tutorials_v500mpdf/6ab0dca96f663bbd36b04376.png)

_The completed render passes_

The frame graph reflects that the Object ID render pass sends idTexture to the Forward Render Pass, which draws to the view’s drawable texture. Note that the GPU only passes textures to the next render pass that are marked Store.

Now that you know how to render textures in different render passes, you can move on to more complex rendering and add some shadows in the next chapter.

<a id="page-325"></a>

## **Key Points**

• A render pass descriptor describes all of the textures and load and store actions needed by a render pass.

• Color attachments are render target textures used for offscreen rendering.

• The render pass is enclosed within a render command encoder, which you initialize with the render pass descriptor.

• You set a pipeline state object on the render command encoder. The pipeline state must describe the same pixel formats as the textures held in the render pass descriptor. If there is no texture, the pixel format must be invalid.

• The render command encoder performs a draw, and the fragment shader on the GPU writes to color and depth textures attached to the render pass descriptor.

• Color attachments don’t have to be rgb colors. Instead, you can write uint or float values in the fragment function.

• For each texture, you describe load and store actions. If you aren’t using a texture in a later render pass, the action should be dontCare so the GPU can discard it and free up memory.

• The GPU workload capture shows you a frame graph where you can see how all your render passes chain together.

<a id="page-326"></a>

# 13

# Chapter 13: Shadows

In this chapter, you’ll learn about shadows. A shadow represents the absence of light on a surface. When light shines on an object, it casts a shadow on anything behind it. Adding shadows in a project makes your scene look more realistic and provides a feeling of depth.

<a id="page-327"></a>

## **Shadow Maps**

Shadow maps are textures containing the information you need to create shadows for a scene. Typically, you render the scene from your camera’s location. However, to build a shadow map, you need to render your scene from the light source’s location - in this case, the sun.

![Figure](Metal_by_Tutorials_v500mpdf/11d66abd810fe04e62d2070e.png)

_A scene render_

The image on the left shows a render from the camera’s position with the directional light pointing down. The image on the right shows a render from the directional light’s position. The eye shows the camera’s position in the first image.

You’ll do two render passes:

![Figure](Metal_by_Tutorials_v500mpdf/f7b6b1dd1096394e07cef63d.png)

_Two render passes are needed_

<a id="page-328"></a>

• First pass: You’ll render from the light’s point of view. Since the sun is directional, you’ll use an orthographic camera rather than a perspective camera. You’re only interested in the depth of objects that the sun can see, so you won’t render a color texture. In this pass, you’ll only render the shadow map as a depth texture. This is a grayscale texture, with the gray value indicating depth. Black is close to the light, and white is farther away.

• Second pass: You’ll render using the scene camera as usual, but you’ll compare the camera fragment with each shadow map fragment. If the camera fragment’s depth is less than the shadow map fragment at that position, the fragment is in the shadow. The light can see the blue x in the above image, so it isn’t in shadow. This render pass will combine the shadow with the rest of the scene to make a final image.

Why would you need two passes here? Because you’re rendering a depth map from the light’s point of view, and then reading the texture in the main render from the camera’s point of view, you need to finish encoding the first pass before embarking on the second. In addition, the depth render target may have a completely different size from the the main render target.

## **The Starter Project**

➤ In Xcode, open this chapter’s starter project.

The code in the starter project is almost identical to the previous chapter but without the object ID and picking code. The scene now has a visible sun that rotates around the scene’s center as the only light. (Remember that the sun is a directional vector. The sun model in the scene is much closer than the sun really would be!)

A separate Cameras folder now holds the definitions of all the cameras, with an extra file, ShadowCamera.swift that contains a few calculation methods.

The code for rendering the sun is in the Utility folder in DebugModel.swift. You’ll render the sun separately from the scene in ForwardRenderPass so that the sun model isn’t shaded with the rest of the scene.

There are a few extra files containing code the app doesn’t need yet. You’ll learn about these files as you proceed through the chapter.

<a id="page-329"></a>

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/52c2be7f97b29f9b1a939dda.png)

_The starter app_

Without shadows, the train and trees in this render appear to float above the ground.

The process for adding the new shadow pass is similar to adding the previous chapter’s object picking render pass:

1. Create the new render pass structure and configure the render pass descriptor, depth stencil state and pipeline state.

2. Declare and draw the render pass in Renderer.

3. Set up the drawing code in the render pass.

4. Set up an orthographic camera from the light’s position and calculate the necessary matrices.

5. Create the vertex shader function to draw vertices from the light’s position.

Although you give the sun a position in this app, as you learned in Chapter 10, “Lighting Fundamentals”, a directional light has a direction rather than a position. So here, you’ll use the sun’s position as a direction.

Note: If you want to see directional lines to debug the sun’s direction, as you did in the earlier chapter, add DebugLights.draw(lights: scene.lighting.lights, encoder: renderEncoder, uniforms: uniforms) to ForwardRenderPass before renderEncoder.endEncoding().

Time to add the new shadow pass.

<a id="page-330"></a>

## **1. Creating the New Render Pass**

➤ In the Render Passes folder, create a new Swift file named ShadowRenderPass.swift, and replace the code with:

```
import MetalKit

struct ShadowRenderPass: RenderPass {
  let label: String = "Shadow Render Pass"
  var descriptor: MTLRenderPassDescriptor?
    = MTLRenderPassDescriptor()
  var depthStencilState: MTLDepthStencilState?
    = Self.buildDepthStencilState()
  var pipelineState: MTLRenderPipelineState
  var shadowTexture: MTLTexture?

  mutating func resize(view: MTKView, size: CGSize) {
  }

  func draw(
    commandBuffer: MTLCommandBuffer,
    scene: GameScene,
    uniforms: Uniforms,
    params: Params
  ) {
  }
}
```

This code creates a render pass that conforms to RenderPass, with a pipeline state and a texture property for the shadow map.

➤ Open Pipelines.swift, and create a new method to create the pipeline state object:

```
static func createShadowPSO() -> MTLRenderPipelineState {
  let vertexFunction =
    Renderer.library?.makeFunction(name: "vertex_depth")
  let pipelineDescriptor = MTLRenderPipelineDescriptor()
  pipelineDescriptor.vertexFunction = vertexFunction
  pipelineDescriptor.colorAttachments[0].pixelFormat = .invalid
  pipelineDescriptor.depthAttachmentPixelFormat = .depth32Float
  pipelineDescriptor.vertexDescriptor = .defaultLayout
  return createPSO(descriptor: pipelineDescriptor)
}
```

<a id="page-331"></a>

Here, you create a pipeline state without a color attachment or fragment function. You’re only interested in the depth information for the shadow — not the color information — so you set the color attachment pixel format to invalid. You’ll still render models, so you still need to hold the vertex descriptor and transform all of the models’ vertices in a vertex function.

➤ Open **ShadowRenderPass.swift**, and create the initializer:

```
init() {
  pipelineState =
    PipelineStates.createShadowPSO()
  shadowTexture = Self.makeTexture(
    size: CGSize(
    width: 2048,
    height: 2048),
    pixelFormat: Renderer.viewDepthPixelFormat,
  label: "Shadow Depth Texture")
}
```

This code initializes the pipeline state object and builds the depth texture with the required pixel format. Unlike other render passes, where you match the view’s size, shadow maps are usually square to match the light’s cuboid orthographic camera, so you don’t need to resize the texture when the window resizes. The resolution should be as much as your game resources budget allows to produce sharper shadows.

## **2. Declaring and Drawing the Render Pass**

➤ In the Renderer folder, open Renderer.swift, and add the new render pass property to Renderer:

`var shadowRenderPass: ShadowRenderPass`

➤ In init(metalView:options:), initialize the render pass before calling super.init().

`shadowRenderPass = ShadowRenderPass()`

➤ In `mtkView(_:drawableSizeWillChange:)`, add:

`shadowRenderPass.resize(view: view, size: size)`

At the moment, because the shadow depth texture is square, you don’t need to resize any textures in shadowRenderPass when the view size changes, but since you’ve already created resize(view:size:) as a required method to conform to RenderPass, and you may add textures later, you should call the method here.

<a id="page-332"></a>

➤ In `draw(scene:in:)`, after `updateUniforms(scene: scene)`, add:

```
shadowRenderPass.draw(
  commandBuffer: commandBuffer,
  scene: scene,
  uniforms: uniforms,
  params: params)
```

This code performs the render pass.

## **3. Setting up the Render Pass Drawing Code**

➤ Open ShadowRenderPass.swift, and add the following code to draw(commandBuffer:scene:uniforms:params:):

```
guard let descriptor = descriptor else { return }
descriptor.depthAttachment.texture = shadowTexture
descriptor.depthAttachment.loadAction = .clear
descriptor.depthAttachment.storeAction = .store

guard let renderEncoder =
  commandBuffer.makeRenderCommandEncoder(descriptor: descriptor)
else {
  return
}
renderEncoder.label = "Shadow Encoder"
renderEncoder.setDepthStencilState(depthStencilState)
renderEncoder.setRenderPipelineState(pipelineState)
for model in scene.models {
  renderEncoder.pushDebugGroup(model.name)
  model.render(
    encoder: renderEncoder,
    uniforms: uniforms,
    params: params)
  renderEncoder.popDebugGroup()
}
renderEncoder.endEncoding()
```

Here, you set the depth attachment texture on the descriptor’s depth attachment. The GPU will clear the texture on loading it and store it so that the following render pass can use it. You then create the render command encoder, using the descriptor, and render the scene as usual.

You surround the model render with renderEncoder.pushDebugGroup(\_:) and renderEncoder.popDebugGroup(), which gathers the render commands into groups on the GPU workload capture. Now, you can more easily debug what’s happening.

<a id="page-333"></a>

## **4. Setting up the Light Camera**

During the shadow pass, you’ll render from the point of view of the sun, so you’ll need a new camera and some new shader matrices.

➤ In Common.h, in the Shaders folder, add these properties to Uniforms:

```
matrix_float4x4 shadowProjectionMatrix;
matrix_float4x4 shadowViewMatrix;
```

Here, you hold the projection and view matrices for the sunlight.

➤ Open Renderer.swift, and add a new property to Renderer:

`var shadowCamera = OrthographicCamera()`

Here, you create an orthographic camera. You previously used an orthographic camera in Chapter 9, “Navigating a 3D Scene”, to render the scene from above. Because sunlight is a directional light, this is the correct projection type for shadows caused by sunlight. However, if you want shadows from a spotlight, you would use a perspective camera with a field of view that matches the spotlight’s cone angle.

➤ Add the following code to the end of updateUniforms(scene:):

```
shadowCamera.viewSize = 16
shadowCamera.far = 16
let sun = scene.lighting.lights[0]
shadowCamera.position = sun.position
```

With this code, you set up the orthographic camera with a cubic view volume of 16 units.

➤ Continue with some more code:

```
uniforms.shadowProjectionMatrix = shadowCamera.projectionMatrix
uniforms.shadowViewMatrix = float4x4(
  eye: sun.position,
  target: .zero,
  up: [0, 1, 0])
```

<a id="page-334"></a>

shadowViewMatrix is a lookAt matrix that ensures the sun is looking at the center of the scene. float4x4(eye:target:up) is defined in MathLibrary.swift. It takes the camera’s position, the point that the camera should look at, and the camera’s up vector. This matrix rotates the camera to look at the target by providing these parameters.

Note: Here’s a useful debugging tip. Temporarily set uniforms.viewMatrix to uniforms.shadowViewMatrix and uniforms.projectionMatrix to uniforms.shadowProjectionMatrix at the end of updateUniforms(scene:). Developers commonly get the shadow matrices wrong, and it’s useful to visualize the scene render through the light.

## **5. Creating the Shader Function**

As you may have noticed when you set up the shadow pipeline state object in Pipelines.swift, it references a shader function named vertex\_depth, which doesn’t exist yet.

➤ In the Shaders folder, using the Metal File template, create a new file named Shadow.metal.

➤ Add the following code to the new file:

```
#import "Common.h"

struct VertexIn {
  float4 position [[attribute(0)]];
};

vertex float4
  vertex_depth(const VertexIn in [[stage_in]],
  constant Uniforms &uniforms [[buffer(UniformsBuffer)]])
{
  matrix_float4x4 mvp =
    uniforms.shadowProjectionMatrix * uniforms.shadowViewMatrix
    * uniforms.modelMatrix;
  return mvp * in.position;
}
```

<a id="page-335"></a>

This code receives a vertex position, transforms it by the light’s projection and view matrices that you set up in Renderer and returns the transformed position.

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/e1689350808e3525db18f947.png)

_No shadow yet_

That looks nice, but where’s the shadow?

➤ Capture the GPU workload and examine the frame capture.

![Figure](Metal_by_Tutorials_v500mpdf/9a9c192ae47711b5b936e0c2.png)

_GPU frame capture_

<a id="page-336"></a>

You currently aren’t forwarding the results of the shadow encoder pass to the forward render pass.

➤ Double-click the shadow encoder pass texture result twice to show the texture in the resource pane.

![Figure](Metal_by_Tutorials_v500mpdf/053061b775a193b94b5d2b9b.png)

_The shadow pass depth texture_

This is the scene rendered from the light’s position. You used the shadow pipeline state, which you configured not to have a fragment shader, so the color information isn’t processed here at all — it’s purely depth. Lighter colors are farther away, and darker colors are closer.

## **The Main Pass**

Now that you have the shadow map saved to a texture, you need to send it to the main pass to use the texture in lighting calculations in the fragment function.

➤ Open **ForwardRenderPass.swift**, and add a new property:

`weak var shadowTexture: MTLTexture?`

➤ In draw(commandBuffer:scene:uniforms:params:), before the model render for loop, add:

`renderEncoder.setFragmentTexture(shadowTexture, index: 15)`

You pass in the shadow texture and send it to the GPU.

<a id="page-337"></a>

➤ Open Renderer.swift, and add this code to draw(scene:in:) before drawing the forward render pass:

`forwardRenderPass.shadowTexture = shadowRenderPass.shadowTexture`

You pass the shadow texture from the previous shadow pass to the forward render pass.

➤ In the Shaders folder, open ShaderDefs.h, and add a new member to VertexOut:

`float4 shadowPosition;`

This holds the vertex position transformed by the shadow matrices.

➤ Open Vertex.metal, and add this line in vertex\_main, when creating out:

```
.shadowPosition =
  uniforms.shadowProjectionMatrix * uniforms.shadowViewMatrix
  * uniforms.modelMatrix * in.position
```

You hold two transformed positions for each vertex. One transformed within the scene from the camera’s point of view, and the other from the light’s point of view. You’ll be able to compare the shadow position with the fragment from the shadow map.

➤ Open Fragment.metal.

This file is where the lighting happens, so the rest of the shadow work will occur in fragment\_main.

➤ First, add one more function parameter after aoTexture:

`depth2d<float> shadowTexture [[texture(15)]]`

Unlike the textures you’ve used in the past, which have a type of texture2d, the texture type of a depth texture is depth2d.

➤ At the end of `fragment_main`, before `return`, add:

```
// shadow calculation
// 1
float3 shadowPosition
  = in.shadowPosition.xyz / in.shadowPosition.w;
// 2
float2 xy = shadowPosition.xy;
xy = xy * 0.5 + 0.5;
xy.y = 1 - xy.y;
```

<a id="page-338"></a>

```
xy = saturate(xy);
// 3
constexpr sampler s(
  coord::normalized, filter::linear,
  address::clamp_to_edge,
  compare_func:: less);
float shadow_sample = shadowTexture.sample(s, xy);
// 4
if (shadowPosition.z > shadow_sample) {
  diffuseColor *= 0.1;
}
```

Here’s a code breakdown:

1. in.shadowPosition represents the vertex’s position from the light’s point of view. The GPU performed a perspective divide before writing the fragment to the shadow texture when you rendered from the light’s point of view. Dividing xyz by w here matches the same perspective division so that you can compare the current sample’s depth value to the one in the shadow texture.

2. Determine a coordinate pair from the shadow position to serve as a screen space pixel locator on the shadow texture. Then, you rescale the coordinates from [-1, 1] to [0, 1] to match the uv space. Finally, you reverse the Y coordinate since it’s upside down.

3. Create a sampler to use with the shadow texture, and sample the texture at the coordinates you just created. Get the depth value for the currently processed pixel. You create a new sampler here, since textureSampler, initialized at the top of the function, repeats the texture if it’s sampled off the edge. Try using textureSampler later to see repeated extra shadows at the back of the scene.

4. You darken the diffuse color for pixels with a depth greater than the shadow value stored in the texture. For example, if shadowPosition.z is 0.5, and shadow\_sample from the stored depth texture is 0.2, then from the sun’s point of view, the current fragment is further away than the stored fragment. Since the sun can’t see the fragment, it’s in shadow.

<a id="page-339"></a>

➤ Build and run the app, and you’ll finally see models with shadows.

![Figure](Metal_by_Tutorials_v500mpdf/c261331a5e8a281225aab61c.png)

_Shadows added_

## **Shadow Acne**

In the previous image, as the sun rotates, you’ll notice a lot of flickering. This is called shadow acne or surface acne. The surface is self-shadowing because of a lack of float precision where the sampled texel doesn’t match the calculated value.

You can mitigate this by adding a bias to the shadow texture, increasing the z value, thereby bringing the stored fragment closer.

➤ Change the conditional test at `// 4` above to:

`if (shadowPosition.z > shadow_sample + 0.001) {`

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/d3384b647397ddd61dd72f5c.png)

_Shadows with no acne_

The surface acne is now gone, and you have clear shadows from the sun as it rotates around the scene.

<a id="page-340"></a>

## **Identifying Problems**

Take a look at the previous render, and you’ll see a problem. Actually, there are two problems. A large dark gray area on the plane appears to be in shadow but shouldn’t be.

Remember the depth texture you examined before:

![Figure](Metal_by_Tutorials_v500mpdf/053061b775a193b94b5d2b9b.png)

_Orthographic camera too large_

The bottom quarter of the image is white, meaning that the depth for that position is at its farthest. The light’s orthographic camera cuts off that part of the plane and causes it to look as if it is in shadow.

The second problem is reading the shadow map.

➤ Open Fragment.metal. In fragment\_main, before xy = saturate(xy);, add:

```
if (xy.x < 0.0 || xy.x > 1.0 || xy.y < 0.0 || xy.y > 1.0) {
  return float4(1, 0, 0, 1);
}
```

The xy texture coordinates should go from 0 to 1 to be on the texture. So if the coordinates are off the texture, you return red.

<a id="page-341"></a>

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/52a68294e55d56e920060d0f.png)

_Reading values off the texture_

Areas in red are off the depth texture.

You can solve these two problems by setting up the light’s orthographic camera to enclose everything the scene camera catches.

## **Visualizing the Problems**

In the Utility folder, DebugCameraFrustum.swift will help you visualize this problem by rendering wireframes for the various camera frustums. When running the app, you can press various keys for debugging purposes:

• 1: The front view of the scene.

• 2: The default view where the sun rotates around the scene.

• 3: Render a wireframe of the scene camera frustum.

• 4: Render a wireframe of the light camera frustum.

• 5: Render a wireframe of the scene camera’s bounding sphere.

This key code is in GameScene’s update(deltaTime:).

<a id="page-342"></a>

➤ Open ForwardRenderPass.swift, and add this to the end of draw(commandBuffer:scene:uniforms:params:), before renderEncoder.endEncoding():

```
DebugCameraFrustum.draw(
  encoder: renderEncoder,
  scene: scene,
  uniforms: uniforms)
```

This code sets up the debug code so that the above keypresses will work.

➤ Open **GameScene.swift**, and at the top of `init()`, add:

`camera.far = 5`

The default for the camera’s far plane is 100, and it’s difficult to visualize. A far of 5 is quite close and easy to visualize but will temporarily cut off a lot of the scene.

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/f546eca2ac00e8ad3c999814.png)

_Some of the scene is missing._

You can see that much of the scene is missing due to the closer far plane.

➤ Press the number `3` key on the keyboard above the letters.

Here, you pause the sun’s rotation and create a new perspective arcball camera that looks down on the scene from afar and renders the original perspective scene camera frustum in blue wireframe.

<a id="page-343"></a>

Using your mouse or trackpad, drag the scene to rotate and examine it. You’ll see that the third tree lies outside the blue frustum and therefore isn’t rendered. You’ll also see where the shadow texture covers the scene. Red areas lie outside the shadow texture.

![Figure](Metal_by_Tutorials_v500mpdf/41642611362197cb123bf13d.png)

_The scene camera frustum_

➤ Press the number `4` key.

The orthographic light’s camera view volume wireframe shows in yellow.

![Figure](Metal_by_Tutorials_v500mpdf/c00a9cf4cb716695500fbcc7.png)

_The light view volume_

One edge of the light’s view volume is from the corners of the gray plane. That’s where the light’s frustum doesn’t reach and shows up on the shadow map texture as white.

<a id="page-344"></a>

➤ In `GameScene`, change `camera.far = 5` to:

`camera.far = 10`

➤ Build and run the app. When you see a patch of red plane, press the 3 key, then the 4 key.

![Figure](Metal_by_Tutorials_v500mpdf/d120623ec5d3c31b0cc2acab.png)

_Understanding why the scene captures area off texture_

Rotating the scene, you’ll see that the blue wireframe extends into the red area. The yellow wireframe should enclose that area but currently doesn’t. So the red area is inside the blue camera frustum, but outside the light volume area.

➤ Press the number `5` key.

This shows a white bounding sphere that encloses the scene camera’s frustum.

![Figure](Metal_by_Tutorials_v500mpdf/fbceed729e33d9a86e85262b.png)

_The scene camera frustum's bounding sphere_

The light volume should enclose the white bounding sphere to get the best shadows.

<a id="page-345"></a>

## **Solving the Problems**

➤ In the Cameras folder, open ShadowCamera.swift. This file contains various methods to calculate the corners of the camera frustum. createShadowCamera(using:lightPosition:) creates an orthographic camera that encloses the specified camera.

➤ Open Renderer.swift. In updateUniforms(scene:), replace all of the shadow code from shadowCamera.viewSize = 16 to the end of the method with:

```
let sun = scene.lighting.lights[0]
shadowCamera = OrthographicCamera.createShadowCamera(
  using: scene.camera,
  lightPosition: sun.position)
uniforms.shadowProjectionMatrix = shadowCamera.projectionMatrix
uniforms.shadowViewMatrix = float4x4(
  eye: shadowCamera.position,
  target: shadowCamera.center,
  up: [0, 1, 0])
```

Here, you create an orthographic light camera with a view volume that completely envelopes the scene.camera’s frustum.

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/bebc4ce3fe5ac4e98fa9a183.png)

_Light view volume encloses scene camera frustum_

<a id="page-346"></a>

Now the light camera volume encloses the whole scene so that you won’t see any red errors or erroneous gray patches.

➤ Open GameScene.swift. In init(), remove:

`camera.far = 10`

You remove the assignment to camera.far, which restores the default camera.far to 100.

➤ Build and run the app.

Due to the huge light view volume, the shadows are very blocky. The image below shows the rendered shadow texture on the right. You can see almost no details.

![Figure](Metal_by_Tutorials_v500mpdf/3ec3e08712a03ef281d746de.png)

_Blocky shadows when the light volume is too large_

You can change far back to 5 or 20 and capture the GPU workload to compare shadow texture quality.

This is one situation where you, as the game designer, would have to decide on the shadow quality. The best outcome would be to use the far value of 5 on shadows closer to the camera and a far value of 20 for shadows farther away, as the resolution won’t matter so much.

<a id="page-347"></a>

## **Cascaded Shadow Mapping**

A better method is cascaded shadow maps which balances performance and shadow depth. In Chapter 8, “Textures”, you learned about mip maps, textures of varying sizes used by the GPU depending on the distance from the camera. Cascaded shadow maps employ a similar idea.

With cascaded shadow maps, you render the scene to several shadow maps in a depth texture array using different near and far planes. As you’ve seen, the smaller far value creates a smaller light volume, which produces a more detailed shadow map. You sample the shadow from the shadow map with the smaller light volume for the fragments closer to the scene camera.

Farther away, you don’t need as much accuracy, so you can sample the shadow from the larger light frustum that takes in more of the scene. The downside is that you have to render the scene multiple times, once for each shadow map.

Shadows can take a lot of calculation and processing time. You have to decide how much of your frame time allowance to give them. In the resources folder for this chapter, references.markdown contains some articles about common techniques to improve your shadows.

<a id="page-348"></a>

## **Key Points**

• A shadow map is a render taken from the point of the light casting the shadow.

• You capture a depth map from the perspective of the light in a first render pass.

• A second render pass then compares the depth of the rendered fragment with the stored depth map fragment. If the fragment is in shadow, you shade the diffuse color accordingly.

• The best shadows are where the light view volume exactly encases the scene camera’s frustum. However, you have to know how much of the scene is being captured. If the area is large, shadows will be blocky.

• Shadows are expensive. A lot of research has gone into rendering shadows, and there are many different methods of improvements and techniques. Cascaded shadow mapping is a common technique.

<a id="page-349"></a>

# 14

# Chapter 14: Deferred Rendering

Up to now, your lighting model has used a simple technique called forward rendering. With traditional forward rendering, you draw each model in turn. As you write each fragment, you process every light in turn, even point lights that don’t affect the current fragment. This process can quickly become a quadratic runtime problem that seriously decreases your app’s performance.

Assume you have a hundred models and a hundred lights in the scene. Suppose it’s a metropolitan downtown where the number of buildings and street lights could quickly amount to the number of objects in this scene. At this point, you’d be looking for an alternative rendering technique.

Deferred rendering, also known as deferred shading or deferred lighting, does two things:

• In the first pass, it collects information such as material, normals and positions from the models and stores them in a special buffer for later processing in the fragment shader. Unnecessary calculations don’t occur in this first pass. The special buffer is named the G-buffer, where G is for Geometry.

• In the second pass, it processes all lights in a fragment shader, but only where the light affects the fragment.

<a id="page-350"></a>

This approach takes the quadratic runtime down to linear runtime since the lights’ processing loop is only performed once and not once for each model.

Look at the forward rendering algorithm:

```
// single pass
for each model {
  for each fragment {
    for each light {
      if directional { accumulate lighting }
      if point { accumulate lighting }
      if spot { accumulate lighting }
    }
  }
}
```

You effected this algorithm in Chapter 10, “Lighting Fundamentals”.

![Figure](Metal_by_Tutorials_v500mpdf/14aafea5ba551dc5fcc9d343.png)

_Point lights affecting fragments_

In forward rendering, you process both lights for the magnified fragments in the image above even though the blue light on the right won’t affect them.

Now, compare it to the deferred rendering algorithm:

```
// pass 1 - g-buffer capture
for each model {
  for each fragment {
    capture color, position, normal and shadow
  }
}
// pass 2 - light accumulation
render a quad
for each fragment { accumulate directional light }
render geometry for point light volumes
for each fragment { accumulate point light }
```

<a id="page-351"></a>

```
render geometry for spot light volumes
for each fragment { accumulate spot light }
```

![Figure](Metal_by_Tutorials_v500mpdf/166703f71fca55df271daa89.png)

_Four textures comprise the G-buffer_

While you have more render passes with deferred rendering, you process fewer lights. All fragments process the directional light, which shades the albedo along with adding the shadow from the directional light. But for the point light, you render special geometry that only covers the area the point light affects. The GPU will process only the affected fragments.

Here are the steps you’ll take throughout this chapter:

• The first pass renders the shadow map. You’ve already done this.

• The second pass constructs G-buffer textures containing these values: material color (or albedo) with shadow information, world space normals and positions.

• Using a full-screen quad, the third and final pass processes the directional light. The same pass then renders point light volumes and accumulates point light information. If you have spotlights, you would repeat this process.

Note: Apple GPUs can combine the second and third passes. Chapter 15, “Tile- Based Deferred Rendering”, will revise this chapter’s project to take advantage of this feature.

<a id="page-352"></a>

## **The Starter Project**

➤ In Xcode, open the starter project for this chapter. The project is almost the same as the end of the previous chapter, with some refactoring and reorganization. There’s new lighting, with extra point lights. The camera and light debugging features from the previous chapter are gone.

Take note of the following additions:

• In the Game folder, in SceneLighting.swift, createPointLights(count:min:max:) creates multiple point lights.

• Since you’ll deal with many lights, the light buffer is greater than 4k. This means that you won’t be able to use MTLRenderCommandEncoder.setFragmentBytes(\_:length:index:). Instead, scene lighting is now split out into three light buffers: one for sunlight, one for point lights and one that contains both sun and point lights, so that forward rendering still works as it did before. Spotlighting and ambient aren’t implemented here.

• In the Render Passes folder, GBufferRenderPass.swift is a copy of ForwardRenderPass.swift and is already set up in Renderer. You’ll work on this render pass and change it to suit deferred rendering. ForwardRenderPass has a debug draw which draws points for the spotlights.

• In the app, a radio button below the metal view gives you the option to switch between render pass types. Aside from the debug draw of the point lights in Forward, there won’t be any difference in the render at this point.

• The lighting is split up into LightingDiffuse.metal and LightingSpecular.metal. In LightingDiffuse.metal, computeDiffuse now processes point lights as well as sun lights in the rendering loop.

• Lighting.metal contains the calculations for sun light, point light and shadows that you learned about in earlier chapters. You’ll add new deferred lighting functions that use these functions.

• Primitive.swift has an option to create an icosahedron, which you’ll use later in the chapter.

<a id="page-353"></a>

➤ Build and run the app to ensure you know how all of the code fits together.

![Figure](Metal_by_Tutorials_v500mpdf/d17d23325e33087e5294ccf9.png)

_The starter app_

The thirty point lights are random, so your render may look slightly different.

## **The G-buffer Pass**

All right, time to build up that G-buffer!

➤ In the Render Passes folder, open GBufferRenderPass.swift, and add four new texture properties to GBufferRenderPass:

```
var albedoTexture: MTLTexture?
var normalTexture: MTLTexture?
var positionTexture: MTLTexture?
var depthTexture: MTLTexture?
```

Those are the textures the G-buffer requires.

➤ Add this code to resize(view:size:):

```
albedoTexture = Self.makeTexture(
  size: size,
  pixelFormat: .bgra8Unorm,
  label: "Albedo Texture")
normalTexture = Self.makeTexture(
  size: size,
  pixelFormat: .rgba16Float,
  label: "Normal Texture")
positionTexture = Self.makeTexture(
  size: size,
  pixelFormat: .rgba16Float,
  label: "Position Texture")
depthTexture = Self.makeTexture(
  size: size,
```

<a id="page-354"></a>

pixelFormat: .depth32Float,   label: &quot;Depth Texture&quot;)

Here, you create the four textures with the desired pixel formats. bgra8Unorm has the format of four 8-bit unsigned components, which store integer values between 0 and 255. However, you’ll need to store the position and normal values in higher precision than the color values by using rgba16Float.

➤ In the Shaders folder, open Common.h, and add a new enumeration for the extra texture indices:

```
typedef enum {
  RenderTargetAlbedo = 1,
  RenderTargetNormal = 2,
  RenderTargetPosition = 3
} RenderTargetIndices;
```

These are the names for the render target texture indices.

In the Geometry folder, open VertexDescriptor.swift, and add the syntactic sugar extension:

```
extension RenderTargetIndices {
  var index: Int {
    return Int(rawValue)
  }
}
```

Using values from `RenderTargetIndices` will now be easier to read.

➤ In the Render Passes folder, open Pipelines.swift.

You’ll create all the pipeline states here. You can compare what each pipeline state requires as you progress through the chapter.

Currently, createGBufferPSO() and createForwardPSO() are the same, but you’ll need to change the G-buffer pipeline state object to specify the different texture formats.

➤ At the end of the file, create a new extension:

```
extension MTLRenderPipelineDescriptor {
  func setGBufferPixelFormats() {
    colorAttachments[RenderTargetAlbedo.index]
      .pixelFormat = .bgra8Unorm
    colorAttachments[RenderTargetNormal.index]
      .pixelFormat = .rgba16Float
    colorAttachments[RenderTargetPosition.index]
```

<a id="page-355"></a>

```
      .pixelFormat = .rgba16Float
  }
}
```

These color attachment pixel formats are the same as the ones you used for the albedo, normal and position textures.

➤ In `createGBufferPSO()`, replace:

```
pipelineDescriptor.colorAttachments[0].pixelFormat =
  Renderer.viewColorPixelFormat
```

➤ With:

```
pipelineDescriptor.colorAttachments[0].pixelFormat = .invalid
pipelineDescriptor.setGBufferPixelFormats()
```

This sets the three color attachment pixel formats. Notice that you’re not using colorAttachments[0] any more, as RenderTargetIndices starts at 1. You could use 0 for the albedo since you’re not using the drawable in this pass, but you’ll combine passes in the next chapter, so you leave color attachment 0 available for this event.

For the vertex function, you can reuse vertex\_main from the main render pass, as all this does is transform the positions and normals. However, you’ll need a new fragment function that stores the position and normal data into textures and doesn’t process the lighting.

➤ Still in `createGBufferPSO()`, replace `"fragment_main"` with:

`"fragment_gBuffer"`

That completes the pipeline state object setup. Next, you’ll deal with the render pass descriptor.

➤ Open GBufferRenderPass.swift, and add this code to the end of init(view:):

`descriptor = MTLRenderPassDescriptor()`

Here, you create a new render pass descriptor instead of using the view’s automatically-generated render pass descriptor.

<a id="page-356"></a>

➤ At the top of `draw(commandBuffer:scene:uniforms:params:)`, add:

```
let textures = [
  albedoTexture,
  normalTexture,
  positionTexture
]
for (index, texture) in textures.enumerated() {
  let attachment =
    descriptor?.colorAttachments[RenderTargetAlbedo.index +
index]
  attachment?.texture = texture
  attachment?.loadAction = .clear
  attachment?.storeAction = .store
  attachment?.clearColor =
    MTLClearColor(red: 0.73, green: 0.92, blue: 1, alpha: 1)
}
descriptor?.depthAttachment.texture = depthTexture
descriptor?.depthAttachment.storeAction = .dontCare
```

You iterate through each of the three textures that you’ll write in the fragment function and add them to the render pass descriptor’s color attachments. If the load action is clear when you add the color attachment, you can set the clear color. The scene depicts a sunny day with sharp shadows, so you set the color to sky blue. store ensures that the color textures don’t clear before the next render pass. However, you won’t need the depth attachment after this render pass, so you set this store action to dontCare.

➤ Still in `draw(commandBuffer:scene:uniforms:params:)`, remove:

```
renderEncoder.setFragmentBuffer(
  scene.lighting.lightsBuffer,
  offset: 0,
  index: LightBuffer.index)
```

In the initial pass, you only store the albedo, or base color, and mark fragments as shadowed or not. You don’t need the light buffer to store these values.

Currently, you send the view’s render pass descriptor to GBufferRenderPass. However, you must change this since you created a new descriptor.

<a id="page-357"></a>

➤ Open Renderer.swift. In draw(scene:in:), remove:

`gBufferRenderPass.descriptor = descriptor`

Before you test all of this code, you must create the new fragment shader.

➤ In the Shaders folder, create a new Metal File named Deferred.metal. Add this code to the new file:

```
#import "Lighting.h"
#import "ShaderDefs.h"

fragment float4 fragment_gBuffer(
  VertexOut in [[stage_in]],
  depth2d<float> shadowTexture [[texture(ShadowTexture)]],
  constant Material &material [[buffer(MaterialBuffer)]])
{
  return float4(material.baseColor, 1);
}
```

Here, you take in the results of the vertex function, the shadow texture from the shadow render pass, and the object’s material. You return the base color of the material so that you’ll be able to see something in the render.

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/a81aa597430a0c8833966242.png)

_The current drawable contains randomness_

Currently, you aren’t writing anything to the view’s drawable, only to the G-buffer render pass descriptor textures. So you’ll get something random on your app window. Mine comes out a lovely shade of magenta.

➤ Capture the GPU workload, and click the Command Buffer to see what’s happening there.

<a id="page-358"></a>

You may get an error because you aren’t writing anything to the drawable texture, but ignore that for the moment.

![Figure](Metal_by_Tutorials_v500mpdf/60cdad82355d39262e94c479.png)

_Frame capture with G-buffer textures_

From this result, you can see that you successfully stored the shadow texture from the shadow pass as well as the three color and depth textures from your G-buffer pass, cleared to your sky blue color.

➤ Open Deferred.metal, and add a new structure before fragment\_gBuffer:

```
struct GBufferOut {
  float4 albedo [[color(RenderTargetAlbedo)]];
  float4 normal [[color(RenderTargetNormal)]];
  float4 position [[color(RenderTargetPosition)]];
};
```

These correspond to the pipeline states and render pass descriptor color attachment textures.

➤ Replace `fragment_gBuffer()` with:

```
// 1
fragment GBufferOut fragment_gBuffer(
  VertexOut in [[stage_in]],
  depth2d<float> shadowTexture [[texture(ShadowTexture)]],
  constant Material &material [[buffer(MaterialBuffer)]])
{
  GBufferOut out;
  // 2
  out.albedo = float4(material.baseColor, 1.0);
  // 3
  out.albedo.a = calculateShadow(in.shadowPosition,
shadowTexture);
  // 4
  out.normal = float4(normalize(in.worldNormal), 1.0);
  out.position = float4(in.worldPosition, 1.0);
  return out;
}
```

<a id="page-359"></a>

Here, you:

1. Return GBufferOut from the fragment function instead of only a single color value.

2. Set the albedo texture to the material’s base color.

3. Calculate whether the fragment is in shadow, using the shadow position and the shadow texture. The shadow value is a single float. Since you don’t use the alpha channel of the albedo texture, you can store the shadow value there.

4. Write the normal and position values into the corresponding texture.

➤ Build and run the app, and capture the GPU workload.

![Figure](Metal_by_Tutorials_v500mpdf/e6cbbe950221227b19f31416.png)

_G-buffer textures containing data_

`fragment_gBuffer` now writes to your three color textures.

<a id="page-360"></a>

## **The Lighting Pass**

Up to this point, you rendered the scene to multiple render targets, saving them for later use in the fragment shader. By rendering a full-screen quad, you can cover every pixel on the screen. This lets you process each fragment from your three textures and calculate lighting for each fragment. The results of this composition pass will end up in the view’s drawable.

➤ Inside the Render Passes folder, create a new Swift file named LightingRenderPass. Replace the contents with:

```
import MetalKit

struct LightingRenderPass: RenderPass {
  let label = "Lighting Render Pass"
  var descriptor: MTLRenderPassDescriptor?
  var sunLightPSO: MTLRenderPipelineState
  let depthStencilState: MTLDepthStencilState?
  weak var albedoTexture: MTLTexture?
  weak var normalTexture: MTLTexture?
  weak var positionTexture: MTLTexture?

  func resize(view: MTKView, size: CGSize) {}

  func draw(
    commandBuffer: MTLCommandBuffer,
    scene: GameScene,
    uniforms: Uniforms,
    params: Params
  ) {
  }
}
```

With this code, you add the necessary conformance to RenderPass and the texture properties you need for this consolidation pass.

You’ll accumulate output from all light types when running the lighting pass. Each type of light needs a different fragment function, so you’ll need multiple pipeline states. First, you’ll create a pipeline state object for rendering the sun’s directional light and return later and add a point light pipeline state object.

➤ Open Pipelines.swift, and copy createForwardPSO() to a new method named createSunLightPSO().

Instead of rendering models, you’ll render a quad for the lighting pass. You can define the vertices on the GPU and create a simple vertex function.

<a id="page-361"></a>

➤ In `createSunLightPSO()`, replace `"vertex_main"` with:

`"vertex_quad"`

This vertex function is responsible for positioning the quad vertices.

➤ Replace `"fragment_main"` with:

`"fragment_deferredSun"`

➤ Remove:

```
pipelineDescriptor.vertexDescriptor =
  MTLVertexDescriptor.defaultLayout
```

For this quad, you don’t need the vertex descriptor. If you don’t remove it, the GPU expects many buffers at the various bindings as described by the default vertex descriptor in VertexDescriptor.swift.

➤ Open LightingRenderPass.swift, and add the initializer to LightingRenderPass:

```
init(view: MTKView) {
  sunLightPSO = PipelineStates.createSunLightPSO()
  depthStencilState = Self.buildDepthStencilState()
}
```

Here, you initialize the pipeline state object with your new pipeline state parameters.

➤ In `draw(commandBuffer:scene:uniforms:params:)`, add:

```
guard let descriptor = descriptor,
  let renderEncoder =
    commandBuffer.makeRenderCommandEncoder(
    descriptor: descriptor) else {
      return
}
renderEncoder.label = label
renderEncoder.setDepthStencilState(depthStencilState)
var uniforms = uniforms
renderEncoder.setVertexBytes(
  &uniforms,
  length: MemoryLayout<Uniforms>.stride,
  index: UniformsBuffer.index)
```

<a id="page-362"></a>

Since you’ll draw the quad directly to the screen, you’ll use the view’s current render pass descriptor. You set up the render command encoder as usual with the depth stencil state and vertex uniforms.

➤ After the previous code, add:

```
renderEncoder.setFragmentTexture(
  albedoTexture,
  index: BaseColor.index)
renderEncoder.setFragmentTexture(
  normalTexture,
  index: NormalTexture.index)
renderEncoder.setFragmentTexture(
  positionTexture, index:
  NormalTexture.index + 1)
```

This code passes the three attachments from the G-buffer render pass. Note the laziness of adding one to the index for the position. This is a mistake waiting to happen, and you should name the index at a later time.

➤ Create a new method for processing the sun light:

```
func drawSunLight(
  renderEncoder: MTLRenderCommandEncoder,
  scene: GameScene,
  params: Params
) {
  renderEncoder.pushDebugGroup("Sun Light")
  renderEncoder.setRenderPipelineState(sunLightPSO)
  var params = params
  params.lightCount = UInt32(scene.lighting.sunLights.count)
  renderEncoder.setFragmentBytes(
    &params,
    length: MemoryLayout<Params>.stride,
    index: ParamsBuffer.index)
  renderEncoder.setFragmentBuffer(
    scene.lighting.sunBuffer,
    offset: 0,
    index: LightBuffer.index)
  renderEncoder.drawPrimitives(
    type: .triangle,
    vertexStart: 0,
    vertexCount: 6)
  renderEncoder.popDebugGroup()
}
```

Here, you send the sun light details to the fragment function and draw the six vertices of a quad.

<a id="page-363"></a>

➤ Call this new method at the end of draw(commandBuffer:scene:uniforms:params:):

```
drawSunLight(
  renderEncoder: renderEncoder,
  scene: scene,
  params: params)
renderEncoder.endEncoding()
```

You call the method and end the render pass encoding.

## **Updating Renderer**

Next, you’ll add the new lighting pass to Renderer, and you’ll pass in the necessary textures and render pass descriptor.

➤ Open Renderer.swift, and add a new property to Renderer:

`var lightingRenderPass: LightingRenderPass`

➤ Add this line before super.init():

`lightingRenderPass = LightingRenderPass(view: metalView)`

You initialized the lighting render pass.

➤ Add this line to mtkView(\_:drawableSizeWillChange:):

`lightingRenderPass.resize(view: view, size: size)`

You currently don’t resize any textures in LightingRenderPass. However, it’s a good idea to call the resize method in case you add anything later.

➤ In draw(scene:in:), locate if options.renderChoice == .deferred.

➤ At the end of the conditional closure, add:

```
lightingRenderPass.albedoTexture =
gBufferRenderPass.albedoTexture
lightingRenderPass.normalTexture =
gBufferRenderPass.normalTexture
lightingRenderPass.positionTexture =
gBufferRenderPass.positionTexture
lightingRenderPass.descriptor = descriptor
lightingRenderPass.draw(
  commandBuffer: commandBuffer,
```

<a id="page-364"></a>

scene: scene,   uniforms: uniforms,   params: params)

Here, you pass the textures to the lighting pass and set the render pass descriptor. You then process the lighting render pass. You’ve set up everything on the CPU side. Now it’s time to turn to the GPU.

## **The Lighting Shader Functions**

First, you’ll create a vertex function that will position a quad. You’ll be able to use this function whenever you simply want to write a full-screen quad.

➤ Open **Deferred.metal**, and add an array of six vertices for the quad:

```
constant float3 vertices[6] = {
  float3(-1,  1,  0),    // triangle 1
  float3( 1, -1,  0),
  float3(-1, -1,  0),
  float3(-1,  1,  0),    // triangle 2
  float3( 1,  1,  0),
  float3( 1, -1,  0)
};
```

➤ Add the new vertex function:

```
vertex VertexOut vertex_quad(uint vertexID [[vertex_id]])
{
  VertexOut out {
    .position = float4(vertices[vertexID], 1)
  };
  return out;
}
```

For each of the six vertices, you return the position in the vertices array.

➤ Add the new fragment function:

```
fragment float4 fragment_deferredSun(
  VertexOut in [[stage_in]],
  constant Params &params [[buffer(ParamsBuffer)]],
  constant Light *lights [[buffer(LightBuffer)]],
  texture2d<float> albedoTexture [[texture(BaseColor)]],
  texture2d<float> normalTexture [[texture(NormalTexture)]],
  texture2d<float> positionTexture
    [[texture(NormalTexture + 1)]])
{
```

<a id="page-365"></a>

```
  return float4(1, 0, 0, 1);
}
```

These are standard parameters for a fragment function. For now, you return the color red.

➤ Build and run the app, and you’ll see a red screen, which is an excellent result as this is the color you currently return from fragment\_deferredSun.

![Figure](Metal_by_Tutorials_v500mpdf/d706ca226f58c744e8b733cf.png)

_Returning red from the fragment function_

You can now work out the lighting and make your render a little more exciting.

➤ Replace the contents of `fragment_deferredSun` with:

```
// 1
uint2 coords = uint2(in.position.xy);
float4 albedo = albedoTexture.read(coords);
float3 normal = normalTexture.read(coords).xyz;
float3 worldPosition = positionTexture.read(coords).xyz;

// 2
Material material {
  .baseColor = albedo.xyz,
  .ambientOcclusion = 1.0,
  .roughness = 0.5
};

// 3
float3 diffuse = 0;
float3 specular = 0;
for (uint i = 0; i < params.lightCount; i++) {
  Light light = lights[i];
  diffuse += calculateSunDiffuse(light, normal, params,
material);
  float3 viewDirection = normalize(params.cameraPosition -
worldPosition);
  specular += calculateSunSpecular(light, material,
viewDirection, normal);
```

<a id="page-366"></a>

```
}
diffuse *= albedo.a;
return float4(diffuse + specular, 1);
```

Here, you read in textures and make the usual light calculations. Things to note:

1. Since the quad is the same size as the screen, in.position matches the screen position, so you can use it as coordinates for reading the textures.

2. For simplicity, the roughness and ambient occlusion are hard coded. For better shading, material values should be captured in the previous G-buffer pass.

3. You receive three sun lights from GBufferRenderPass, so you calculate all the sun light contribution to the diffuse and specular colors with the values you read from the textures. After accumulating the diffuse light contribution, you multiply it by the shadow you previously stored in the albedo alpha channel.

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/90dc13edb38559cbbd8839fe.png)

_Accumulating the directional light and shadows_

The result should be the same as the forward render pass, except for the point lights. However, you’ll notice that the sky is a different color. The color changed because you calculate the sunlight for every fragment on the screen, even where there’s no original model geometry. In the next chapter, you’ll deal with this problem by using stencil masks.

This seems a lot of work for not much gain so far. But now comes the payoff!

Instead of rendering just 30 point lights, you’ll render as many as your device can take: in the order of thousands more than the forward renderer.

<a id="page-367"></a>

## **Adding Point Lights**

So far, you’ve drawn the plain albedo and shaded it with directional light. You need a second fragment function for calculating point lights.

In the original forward pass algorithm, you iterated through all the point lights for every fragment and performed the point light accumulation. Now you’ll render a light volume in the shape of a sphere for every point light. Only the fragments you render for that light volume will require the point light accumulation.

The problem comes when one light volume is in front of another. The fragment function result will overwrite any previous result. You’ll overcome this problem by accumulating the result into the final drawable by blending rather than overwriting the fragment.

![Figure](Metal_by_Tutorials_v500mpdf/b30f62bc8edf6cd3096eb8c8.png)

_Blending the light volume_

<a id="page-368"></a>

In Primitive.swift, in the Geometry folder, there’s an option to generate mesh for an icosahedron. You’ll render one of these for each point light.

![Figure](Metal_by_Tutorials_v500mpdf/1c90f37f7fc77cd6d0a1a080.png)

_Icosahedron and UV sphere_

The icosahedron is a low-resolution sphere with twenty-five vertices. Compare it to a UV sphere. The icosahedron’s faces are more regular and all have a similar area, whereas the UV sphere’s faces are smaller at the two top and bottom poles.

This app assumes that all point lights have the same radius attenuation, which fits inside the icosahedron. If a point light has a larger radius, the icosahedron’s straight edges could cut it off. You could also add more vertices to an icosahedron, making it rounder, but that would make the rendering less efficient.

➤ Open LightingRenderPass.swift, and add a new property to LightingRenderPass:

```
var icosahedron = Model(
  name: "icosahedron",
  primitiveType: .icosahedron)
```

You initialize the icosahedron for later use.

Now you need a new pipeline state object with new shader functions to render the icosahedron with its point lighting.

➤ Open Pipelines.swift, and copy createForwardPSO() to a new method called createPointLightPSO().

<a id="page-369"></a>

➤ Change the vertex function’s name to &quot;vertex\_pointLight&quot; and the fragment function’s name to &quot;fragment\_pointLight&quot;.

Later, you’ll need to add blending to the light accumulation. The pipeline state is how you tell the GPU that you require blending, so shortly, you’ll add this to the pipeline state object.

➤ Open LightingRenderPass.swift, and add a new property for the pipeline state object:

`var pointLightPSO: MTLRenderPipelineState`

➤ Initialize the pipeline state in init(view:):

`pointLightPSO = PipelineStates.createPointLightPSO()`

➤ Create a new method to draw the point light volumes:

```
func drawPointLight(
  renderEncoder: MTLRenderCommandEncoder,
  scene: GameScene,
  params: Params
) {
  renderEncoder.pushDebugGroup("Point lights")
  renderEncoder.setRenderPipelineState(pointLightPSO)

  renderEncoder.setVertexBuffer(
    scene.lighting.pointBuffer,
    offset: 0,
    index: LightBuffer.index)
  renderEncoder.setFragmentBuffer(
    scene.lighting.pointBuffer,
    offset: 0,
    index: LightBuffer.index)

  var params = params
  params.lightCount = UInt32(scene.lighting.pointLights.count)
  renderEncoder.setFragmentBytes(
    &params,
    length: MemoryLayout<Params>.stride,
    index: ParamsBuffer.index)
}
```

You send the point lights to both vertex and fragment shaders. The vertex function needs the light position to position each icosahedron, while the fragment function needs the light attenuation and color.

<a id="page-370"></a>

➤ Add this code to the end of drawPointLight(renderEncoder:scene:params:):

```
guard let mesh = icosahedron.meshes.first,
  let submesh = mesh.submeshes.first else { return }
for (index, vertexBuffer) in mesh.vertexBuffers.enumerated() {
  renderEncoder.setVertexBuffer(
    vertexBuffer,
    offset: 0,
    index: index)
}
```

You set up the vertex buffers with the icosahedron’s mesh attributes.

## **Instancing**

If you had one thousand point lights, a draw call to render the geometry for each light volume would bring your system to a crawl. Instancing is a great way to tell the GPU to draw the same geometry a specific number of times. The GPU informs the vertex function which instance it’s currently drawing so that you can extract information from arrays containing instance information.

In SceneLighting, you have an array of point lights with the position and color. Each of these point lights is an instance. You’ll draw the icosahedron mesh for each point light.

➤ After the previous code, add the draw call:

```
renderEncoder.drawIndexedPrimitives(
  type: .triangle,
  indexCount: submesh.indexCount,
  indexType: submesh.indexType,
  indexBuffer: submesh.indexBuffer,
  indexBufferOffset: submesh.indexBufferOffset,
  instanceCount: scene.lighting.pointLights.count)
renderEncoder.popDebugGroup()
```

Adding instanceCount to the draw call means that the GPU will repeat drawing the icosahedron’s vertex and submesh information for the specified number of instances. GPU hardware is optimized to do this.

➤ Call this new method from draw(commandBuffer:scene:uniforms:params:) before renderEncoder.endEncoding():

```
drawPointLight(
  renderEncoder: renderEncoder,
  scene: scene,
  params: params)
```

<a id="page-371"></a>

## **Creating the Point Light Shader Functions**

➤ Open Deferred.metal, and add the new structures that the vertex function will need:

```
struct PointLightIn {
  float4 position [[attribute(Position)]];
};

struct PointLightOut {
  float4 position [[position]];
  uint instanceId [[flat]];
};
```

You’re only interested in the position, so you only use the vertex descriptor’s position attribute.

You send the position to the rasterizer, but you also send the instance ID so that the fragment function can extract the light details from the point lights array. You don’t want any rasterizer interpolation, so you mark the instance ID with the attribute [[flat]].

➤ Add the new vertex function:

```
vertex PointLightOut vertex_pointLight(
  PointLightIn in [[stage_in]],
  constant Uniforms &uniforms [[buffer(UniformsBuffer)]],
  constant Light *lights [[buffer(LightBuffer)]],
  // 1
  uint instanceId [[instance_id]])
{
  // 2
  float4 lightPosition = float4(lights[instanceId].position, 0);
  float4 position =
    uniforms.projectionMatrix * uniforms.viewMatrix
  // 3
    * (in.position + lightPosition);
  PointLightOut out {
    .position = position,
    .instanceId = instanceId
  };
  return out;
}
```

The points of interest are:

1. Use the attribute [[instance\_id]] to detect the current instance.

2. Use the instance ID to index into the lights array.

<a id="page-372"></a>

3. Add the light’s position to the vertex position. Since you’re not dealing with scaling or rotation, you don’t need to multiply by a model matrix.

➤ Add the new fragment function:

```
fragment float4 fragment_pointLight(
  PointLightOut in [[stage_in]],
  constant Params &params [[buffer(ParamsBuffer)]],
  texture2d<float> normalTexture [[texture(NormalTexture)]],
  texture2d<float> positionTexture
    [[texture(NormalTexture + 1)]],
  constant Light *lights [[buffer(LightBuffer)]])
{
// 1
  uint2 coords = uint2(in.position.xy);
  float3 normal = normalTexture.read(coords).xyz;
  float3 worldPosition = positionTexture.read(coords).xyz;
// 2
  Material material {
    .baseColor = 1
  };
// 3
  Light light = lights[in.instanceId];
  float3 color = calculatePointDiffuse(
    light,
    normal,
    material,
    worldPosition);
// 4
  color *= 0.3;
  return float4(color, 1);
}
```

Going through the code:

1. Just as you did for the sun light, you read in the textures from the previous render pass.

2. The base color for the icosahedron is 1. Rather than taking the color from the albedo, this time, you’ll achieve the glowing point light with GPU blending.

3. You extract the light from the lights array using the instance ID sent by the vertex function.  and calculate the point lighting. In this case, you don’t iterate through all the point lights, as you accumulate the lighting for each point light when you render each icosahedron.

4. You reduce the intensity by 0.3, as blending will make the lights brighter.

➤ Build and run the app. Your render is as before. No glowing point lights here.

<a id="page-373"></a>

Capture the GPU workload and check out the attachments in the Point lights render encoder section:

![Figure](Metal_by_Tutorials_v500mpdf/fbccb27b718bb9f30bcaf5e1.png)

_Point light volume drawing_

The icosahedrons are drawing, but if you check the depth attachment with the magnifier, you’ll see all the values are zero. There’s a problem with the depth: the icosahedrons are not rendering in front of the quad.

➤ Open **LightingRenderPass.swift**, and add a new method:

```
static func buildDepthStencilState() -> MTLDepthStencilState? {
  let descriptor = MTLDepthStencilDescriptor()
  descriptor.isDepthWriteEnabled = false
  return Renderer.device.makeDepthStencilState(descriptor:
descriptor)
}
```

This code overrides the default RenderPass protocol method. You disable depth writes because you always want the icosahedrons to render.

<a id="page-374"></a>

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/ee37652837629cc4cf289d89.png)

_Rendering icosahedrons_

Your icosahedron volumes now render in front of the quad.

## **Blending**

➤ Open Pipelines.swift. In createPointLightPSO(), add this code before return:

```
let attachment = pipelineDescriptor.colorAttachments[0]
attachment?.isBlendingEnabled = true
attachment?.rgbBlendOperation = .add
attachment?.alphaBlendOperation = .add
attachment?.sourceRGBBlendFactor = .one
attachment?.sourceAlphaBlendFactor = .one
attachment?.destinationRGBBlendFactor = .one
attachment?.destinationAlphaBlendFactor = .zero
attachment?.sourceRGBBlendFactor = .one
attachment?.sourceAlphaBlendFactor = .one
```

<a id="page-375"></a>

Here, you enabled blending. You shouldn’t have this on by default because blending is an expensive operation. The other properties determine how to combine the source and destination fragments.

All these blending properties are at their defaults, except for destinationRGBBlendFactor. They’re written out here in full to show what you can change. The important change is destinationRGBBlendFactor from zero to one, so blending will occur.

The icosahedrons will blend with the color already drawn in the background quad. Black will disappear, leaving only the light color.

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/a4e16feeb386fd29429d76e5.png)

_A few point lights rendering_

Now it’s time to crank up those point lights. Be careful when you switch to the forward renderer. If you have a lot of lights, your system will appear to hang while the forward render pass laboriously calculates the point light effect on each fragment.

➤ Open SceneLighting.swift. In init(), replace:

```
pointLights = Self.createPointLights(
  count: pointLightsCount,
  min: [-3, 0.1, -3],
  max: [3, 0.3, 3])
```

<a id="page-376"></a>

➤ With:

```
pointLights = Self.createPointLights(
  count: 200,
  min: [-6, 0.1, -6],
  max: [6, 0.3, 6])
```

With this code, you create 200 point lights, changing the minimum and maximum xyz values to constrain the lights a larger area.

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/0828568c07e14b331f293d34.png)

_Two hundred point lights_

Your point lights blend beautifully and are comparable with the forward renderer. The only problem is the color of the sky, which you’ll fix in the following chapter.

➤ On the Debug navigator, check your FPS for both Deferred and Forward. For 200 lights, on my iPad Mini 6, I have 25 FPS for Forward rendering, versus 60 FPS for Deferred. (Remember to remove the Debug draw from ForwardRenderPass to compare like with like.)

➤ If you are running on macOS, continue gradually increasing count in the previous code until your forward pass FPS decreases below 60 FPS. Make a note of the number of lights for comparison.

<a id="page-377"></a>

➤ Increase count and check how many point lights your deferred render can manage before degrading below 60 FPS. Many lights are so bright that you may have to dial down the light color in createPointLights(count:min:max:) with light.intensity = 0.5.

![Figure](Metal_by_Tutorials_v500mpdf/c016613a9baf756f031ac5c4.png)

_Render algorithm comparison_

On M1 Max MacBook Pro, performance in a small window starts degrading on the forward renderer at about 250 lights, whereas the deferred renderer can cope with 8,000 lights. With the window maximized, forward rendering starts degrading at about 30 lights, whereas the deferred renderer manages more than ten times that.

This chapter has opened your eyes to two rendering techniques: forward and deferred. As the game designer, you get to choose your rendering method. Forward and deferred rendering are just two: Several other techniques can help you get the most out of your frame time.

There are also many ways of configuring your forward and deferred render passes. references.markdown in the resources folder for this chapter has a few links for further research.

In the next chapter, you’ll learn how to make your deferred render pass more efficient by taking advantage of Apple Silicon’s tile-based deferred rendering (TBDR) architecture.

<a id="page-378"></a>

## **Key Points**

• Forward rendering processes all lights for all fragments.

• Deferred rendering captures albedo, position and normals for later light calculation. For point lights, only the necessary fragments are rendered.

• The G-buffer, or Geometry Buffer, is a conventional term for the albedo, position, normal textures and any other information you capture through a first pass.

• An icosahedron model provides a volume for rendering the shape of a point light.

• Using instancing, the GPU can efficiently render the same geometry many times.

• The pipeline state object specifies whether the result from the fragment function should be blended with the currently attached texture.

<a id="page-379"></a>

# 15

# Chapter 15: Tile-Based Deferred Rendering

Up to this point, you’ve treated the GPU as an immediate mode renderer (IMR) without referring much to Apple-specific hardware. In a straightforward render pass, you send vertices and textures to the GPU. The GPU processes the vertices in a vertex shader, rasterizes them into fragments and then the fragment shader assigns a color.

![Figure](Metal_by_Tutorials_v500mpdf/5fea49d085103a3dea9dae82.png)

_Immediate mode pipeline_

<a id="page-380"></a>

A traditional GPU uses system memory to transfer resources between passes where you have multiple passes.

![Figure](Metal_by_Tutorials_v500mpdf/4571b3012c417d68966e4aad.png)

_Immediate mode using system memory_

Apple’s Silicon uses a tile-based deferred rendering (TBDR) architecture. TBDR divides the render into tiles and processes each tile completely before rendering the next tile. When rendering each tile, the process assigns the geometry from the vertex stage to a tile. It then forwards each tile to the rasterizer. Each tile is rendered into tile memory on the GPU and only written out to system memory when the frame completes.

![Figure](Metal_by_Tutorials_v500mpdf/1b7c509101cbb6cf1e7d849e.png)

_TBDR pipeline_

<a id="page-381"></a>

## **Programmable Blending**

Instead of writing the texture in one pass and reading it in the next pass, tile memory enables programmable blending. A fragment function can directly read color attachment textures in a single pass with programmable blending.

![Figure](Metal_by_Tutorials_v500mpdf/a94ddf205bbde58006ddfd77.png)

_Programmable blending with memoryless textures_

The G-buffer doesn’t have to transfer the temporary textures to system memory anymore. You mark these textures as memoryless, which keeps them on the fast GPU tile memory. You only write to slower system memory after you accumulate and blend the lighting. This speeds up rendering because you use less bandwidth.

## **Tiled Deferred Rendering**

Confusingly, tiled deferred rendering can apply to the deferred rendering or shading technique as well as the name of an architecture. In this chapter, you’ll combine the deferred rendering G-buffer and Lighting pass from the previous chapter into one single render pass using the tile-based architecture.

To complete this chapter, you need to run the code on a device with an Apple GPU. This device could be an Apple Silicon macOS device or any iOS device capable of running the latest iOS. Simulator and Intel Macs do not support reading from render targets, but the starter project will run Forward Rendering in place of Tiled Deferred Rendering instead of crashing.

<a id="page-382"></a>

## **The Starter Project**

➤ In Xcode, open the starter project for this chapter.

This project is the same as the end of the previous chapter, except:

• In the SwiftUI Views folder, there’s a new option for tiledDeferred in Options.swift. Renderer will update tiledSupported depending on whether the device supports tiling.

• In the Render Passes folder, the deferred rendering pipeline state creation methods in Pipelines.swift have an extra Boolean parameter of tiled:. Later, you’ll assign a different fragment function depending on this parameter.

• A new file, TiledDeferredRenderPass.swift, combines GBufferRenderPass and LightingRenderPass into one long file. The code is substantially similar, with the two render passes combined into draw(commandBuffer:scene:uniforms:params:). You’ll convert this file from the immediate mode deferred rendering algorithm to tile-based deferred rendering.

• Renderer instantiates TiledDeferredRenderPass if the device supports tiling.

➤ Build and run the app on your TBDR device.

![Figure](Metal_by_Tutorials_v500mpdf/bbcb4a64fcde29923fe32d10.png)

_The starter app_

The render is the same as at the end of the previous chapter but with an added Tiled Deferred option under the Metal view.

Note: If you run the app on a non-TBDR device, the option will be marked Tiled Deferred not Supported!.

<a id="page-383"></a>

Apple assigns GPU families to chips. The latest M4-series is Apple9. When using newer Metal features, use device.supportsFamily(\_:) to check whether the current device supports the capabilities you’re requesting.

In init(metalView:options:), Renderer checks the GPU family. If the device supports Apple family 3 GPUs, which Apple introduced with the A9 chip, it supports tile-based deferred rendering.

Note: You can see the list of Apple Families and available features in the Metal Feature Set Tables document (https://is.gd/52uVY9).

## **The G-buffer Render Pass**

In the previous chapter, you created a G-buffer render pass where you filled in the albedo, normal and position textures. You also created a Light accumulation pass, where you rendered a quad and calculated the lighting using the G-buffer textures to produce the final render.

![Figure](Metal_by_Tutorials_v500mpdf/e82ba9593d9742c114c314e3.png)

_The G-buffer render pass and accumulation_

➤ In the Render Passes folder, open TiledDeferredRenderPass.swift and examine the code. draw(commandBuffer:scene:uniforms:params:) contains both the G-buffer pass and the Lighting pass. There’s a lot of code, but you should recognize it from the previous chapter.

<a id="page-384"></a>

➤ Currently, this is what happens during your render passes:

![Figure](Metal_by_Tutorials_v500mpdf/5a61b36533d18e3ca38bf534.png)

_Starter app render passes_

The GPU renders your G-buffer textures using its tile memory, but then writes the textures to system memory. In the next render pass, the GPU reads them back from system memory.

These are the steps you’ll take to eliminate the extra system memory read/write:

1. Change the texture storage mode from private to memoryless.

2. Change the descriptor’s color attachment store action for all the G-buffer textures to dontCare.

3. In the Lighting pass, stop sending the color attachment textures to the fragment function.

4. Create new fragment shaders for rendering the sun and point lights.

5. Combine the two render encoder passes with their descriptors into one.

6. Update the pipeline state objects to match the new render pass descriptor.

As you work through the chapter, you’ll encounter common errors so you can learn how to fix them when you make them in the future.

<a id="page-385"></a>

## **1. Making the Textures Memoryless**

➤ Open TiledDeferredRenderPass.swift. In resize(view:size:), change the storage mode for all four textures from storageMode: private to:

`storageMode: .memoryless`

The memoryless storage mode means that the texture will only exist in tile memory.

➤ Build and run the app.

You’ll get an error in the debug console: Memoryless attachment content cannot be stored in memory. You’re still storing the attachment back to system memory. Time to fix that.

## **2. Changing the Store Action**

➤ Stay in TiledDeferredRenderPass.swift. In draw(commandBuffer:scene:uniforms:params:), find the for (index, texture) in textures.enumerated() loop and change attachment?.storeAction = .store to:

`attachment?.storeAction = .dontCare`

This line stops the textures from transferring to system memory.

➤ Build and run the app.

You’ll get another error: failed assertion \`Set Fragment Buffers Validationtexture is Memoryless, and cannot be assigned.\`. For the Lighting pass, you send the textures to the fragment shader as texture parameters. However, you can’t do that with memoryless textures because they’re only resident in tile memory. You’ll fix that next.

## **3. Removing the Fragment Textures**

➤ In drawLightingRenderPass(renderEncoder:scene:uniforms:params:), remove:

```
renderEncoder.setFragmentTexture(
  albedoTexture,
  index: BaseColor.index)
renderEncoder.setFragmentTexture(
  normalTexture,
```

<a id="page-386"></a>

```
  index: NormalTexture.index)
renderEncoder.setFragmentTexture(
  positionTexture,
  index: PositionTexture.index)
```

➤ Build and run the app.

You’ll probably get a black screen now because your deferred shader functions are expecting textures.

## **4. Creating the New Fragment Functions**

➤ Still in TiledDeferredRenderPass.swift, in init(view:), change the three pipeline state objects’ tiled: false parameters to:

`tiled: true`

➤ Open Pipelines.swift. In createSunLightPSO(tiled:) and createPointLightPSO(tiled:), check which fragment functions you need to create:

• fragment\_tiled\_deferredSun

• fragment\_tiled\_pointLight

You can still use the same vertex functions and G-buffer fragment function.

➤ In the Shaders folder, open Deferred.metal.

➤ Copy fragment\_deferredSun to a new function called fragment\_tiled\_deferredSun.

➤ In fragment\_tiled\_deferredSun, since you’re not sending the fragment textures to the fragment function any more, remove the parameters:

```
texture2d<float> albedoTexture [[texture(BaseColor)]],
texture2d<float> normalTexture [[texture(NormalTexture)]],
texture2d<float> positionTexture [[texture(PositionTexture)]]
```

➤ Add a new parameter:

`GBufferOut gBuffer`

GBufferOut is the structure that refers to the color attachment render target textures.

<a id="page-387"></a>

➤ Change:

```
uint2 coords = uint2(in.position.xy);
float4 albedo = albedoTexture.read(coords);
float3 normal = normalTexture.read(coords).xyz;
float3 worldPosition = positionTexture.read(coords).xyz;
```

➤ To:

```
float4 albedo = gBuffer.albedo;
float3 normal = gBuffer.normal.xyz;
float3 worldPosition = gBuffer.position.xyz;
```

You no longer have to look up coordinates, or read textures, as you have access to the fast GPU tile memory for this fragment.

Repeat this process for the point lights:

➤ Copy fragment\_pointLight to a new function named fragment\_tiled\_pointLight

➤ Remove the parameters:

```
texture2d<float> normalTexture [[texture(NormalTexture)]],
texture2d<float> positionTexture [[texture(PositionTexture)]],
```

➤ Add the parameter:

`GBufferOut gBuffer`

➤ Change:

```
uint2 coords = uint2(in.position.xy);
float3 normal = normalTexture.read(coords).xyz;
float3 position = positionTexture.read(coords).xyz;
```

➤ To:

```
float3 normal = gBuffer.normal.xyz;
float3 worldPosition = gBuffer.position.xyz;
```

➤ Build and run the app.

When creating the sun light pipeline state, you now get the error: Shaders reads from a color attachment whose pixel format is MTLPixelFormatInvalid.

<a id="page-388"></a>

To explain this error, the following image shows the attachments you set up in the two render passes in the previous chapter’s Deferred Rendering:

![Figure](Metal_by_Tutorials_v500mpdf/3a888867a9600be138bc3286.png)

_Render pass descriptor color attachments_

Currently, when writing the G-buffer in fragment\_gBuffer, you only write to color attachments 1 (albedo), 2 (normal) and 3 (position). Your render pass descriptor colorAttachments[0] is nil, and your pipeline state colorAttachments[0] pixel format is invalid.

However, when accumulating the lighting, in Pipelines.swift, in createSunLightPSO(tiled:), you only set up colorAttachments[0], and not [1], [2] and [3]. This means that when fragment\_tiled\_deferredSun reads from gBuffer, the other color attachment pixel formats are currently invalid.

Instead of using two render pass descriptors and render command encoders, you’ll configure the view’s current render pass descriptor to use all the color attachments. Then you’ll set up the pipeline state configuration to match.

## **5. Combining the Two Render Passes**

➤ Open TiledDeferredRenderPass.swift. In draw(commandBuffer:scene:uniforms:params:), change let descriptor = MTLRenderPassDescriptor() to:

`let descriptor = viewCurrentRenderPassDescriptor`

You’ll use the view’s current render pass descriptor, passed in from Renderer, to configure your render command encoder.

<a id="page-389"></a>

➤ Still in `draw(commandBuffer:scene:uniforms:params:)`, remove:

```
renderEncoder.endEncoding()

// MARK: Lighting pass
// Set up Lighting descriptor
guard let renderEncoder =
  commandBuffer.makeRenderCommandEncoder(
    descriptor: viewCurrentRenderPassDescriptor) else {
  return
}
```

Here, you remove the second render command encoder.

## **6. Updating the Pipeline States**

➤ Open Pipelines.swift. Add this code to both createSunLightPSO(tiled:) and createPointLightPSO(tiled:) after setting colorAttachments[0].pixelFormat:

```
if tiled {
  pipelineDescriptor.setGBufferPixelFormats()
}
```

This code sets the color pixel formats to match the render target textures.

➤ In createGBufferPSO(tiled:), after setting colorAttachments[0].pixelFormat, add:

```
if tiled {
  pipelineDescriptor.colorAttachments[0].pixelFormat
    = Renderer.viewColorPixelFormat
}
```

In the previous chapter, your G-buffer render pass descriptor had no texture in colorAttachments[0]. However, when you use the view’s current render pass descriptor, colorAttachment[0] stores the view’s current drawable texture, so you match that texture’s pixel format.

<a id="page-390"></a>

Now you store the textures in tile memory and use a single render pass.

![Figure](Metal_by_Tutorials_v500mpdf/7431dc32289382578744faf4.png)

_A single render pass_

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/f07c23211cd69c94e09f099c.png)

_The final render_

Finally, you’ll see the result you want. The render is the same whether you choose Tiled Deferred or Deferred.

<a id="page-391"></a>

➤ With the Tiled Deferred option selected, capture the GPU workload. You’ll see that all your textures, aside from the shadow pass, process in the single render pass.

![Figure](Metal_by_Tutorials_v500mpdf/4b2eed722bf4535456b03d5e.png)

_The final frame capture_

Your four memoryless render target textures show up as // Don’t care on the capture. When you select a texture, the storage mode shows as Memoryless, proving they aren’t taking up any system memory.

Now for the exciting part — to see how this has affected your frame resource usage.

➤ Run your app in as large a window as possible and show the Debug navigator. In your app, don’t select Deferred yet.

➤ On the Debug navigator, take note of the **Memory** used.

![Figure](Metal_by_Tutorials_v500mpdf/2529d993d50a35ceea4f7af7.png)

_Tile Deferred memory used full-screen_

<a id="page-392"></a>

You initialize all textures at the start of the app. But, as you haven’t yet selected Deferred, the Deferred render pass textures haven’t yet been used. This means they don’t yet take up memory.

➤ In your app, select Deferred, and notice how the memory used by your app leaps up.

![Figure](Metal_by_Tutorials_v500mpdf/ca62d17738f40afd4b9e7966.png)

_Deferred memory used full-screen_

The textures used by the deferred G-buffer render pass are held in system memory, and thus take up a large percentage of your app’s memory resources. Whereas the memoryless textures used by TBDR don’t contribute to the app’s memory usage.

In an app that uses many render targets and many textures, using memoryless textures can save enormous amounts of system memory and bandwidth.

## **Stencil Tests**

The last step in completing your deferred rendering is to fix the sky. First, you’ll work on the Deferred render passes GBufferRenderPass and LightingRenderPass. Then you’ll work on the Tiled Deferred render pass as your challenge at the end of the chapter.

Currently, when you render the quad in the lighting render pass, you accumulate the directional lighting on all the quad’s fragments. Wouldn’t it be great to only process fragments where model geometry is rendered?

<a id="page-393"></a>

Fortunately, that’s what stencil testing was designed to do. In the following image, the stencil texture is on the right. The black area should mask the image so that only the white area renders.

![Figure](Metal_by_Tutorials_v500mpdf/0056b8770cdc652b6801487a.png)

_Stencil testing_

As you already know, part of rasterization is performing a depth test to ensure the current fragment is in front of any fragments already rendered. The depth test isn’t the only test the fragment has to pass. You can configure a stencil test.

Up to now, when you created the MTLDepthStencilState, you only configured the depth test. In the pipeline state objects, you set the depth pixel format to depth32float with a matching depth texture.

A stencil texture consists of 8-bit values, from 0 to 255. You’ll add this texture to the depth buffer so that the depth buffer will consist of both depth texture and stencil texture.

For a better understanding of the stencil buffer, examine the following image.

![Figure](Metal_by_Tutorials_v500mpdf/e8696de6a2888823aecf2c2e.png)

_A stencil texture_

<a id="page-394"></a>

In this scenario, the buffer is initially cleared with zeros. When the pink triangle renders, the rasterizer increments the fragments the triangle covers. The second yellow triangle renders, and the rasterizer again increments the fragments that the triangle covers.

## Stencil Test Conﬁguration

All rendered fragments must pass both the depth and the stencil test that you configure.

As part of the configuration you set:

• The comparison function.

• The operation on pass or fail.

• A read and write mask.

Take a closer look at the comparison function.

## **1. The Comparison Function**

When the rasterizer performs a stencil test, it compares a reference value with the value in the stencil texture using a comparison function. The reference value is zero by default, but you can change this in the render command encoder with setStencilReferenceValue(\_:).

The comparison function is a mathematical comparison operator, such as equal or lessEqual. A comparison function of always will let the fragment pass the stencil test, whereas with a stencil comparison of never, the fragment will always fail.

For instance, if you want to use the stencil buffer to mask out the yellow triangle area in the previous example, you could set a reference value of 2 in the render command encoder and then set the comparison to notEqual. Only fragments that don’t have their stencil buffer set to 2 will pass the stencil test.

<a id="page-395"></a>

## **2. The Stencil Operation**

Next, you set the stencil operations to perform on the stencil buffer. There are three possible results to configure:

• Stencil test failure.

• Stencil test pass and depth failure.

• Stencil test pass and depth pass.

The default operation for each result is keep, which doesn’t change the stencil buffer.

Other operations include:

• incrementClamp: The stencil buffer increments the stencil buffer fragment until the maximum of 255.

• incrementWrap: The stencil buffer increments the stencil buffer fragment and, if necessary, wraps around from 255 to 0.

• decrementClamp and decrementWrap: The same as increment, except the stencil buffer value decreases.

• invert: Performs a bitwise NOT operation, which inverts all of the bits.

• replace: Replaces the stencil buffer fragment with the reference value.

To get the stencil buffer to increase when a triangle renders in the previous example, you perform the incrementClamp operation when the fragment passes the depth test.

## **3. The Read and Write Mask**

There’s one more wrinkle. You can specify a read mask and a write mask. By default, these masks are 255 or 11111111 in binary. When you test a bit value against 1, the value doesn’t change.

Now that you have the concept and principles under your belt, it’s time to learn what all this means.

<a id="page-396"></a>

## **Create the Stencil Texture**

The stencil texture buffer is an extra 8-bit buffer attached to the depth texture buffer. You optionally configure it when you configure the depth buffer.

➤ Open Pipelines.swift. In createGBufferPSO(tiled:), after pipelineDescriptor.depthAttachmentPixelFormat = Renderer.viewDepthPixelFormat, add:

```
if !tiled {
  pipelineDescriptor.depthAttachmentPixelFormat
    = .depth32Float_stencil8
  pipelineDescriptor.stencilAttachmentPixelFormat
    = .depth32Float_stencil8
}
```

This code configures both the depth and stencil attachment to use one texture, including the 32-bit depth and the 8-bit stencil buffers.

➤ Open GBufferRenderPass.swift. In resize(view:size:), change depthTexture to:

```
depthTexture = Self.makeTexture(
  size: size,
  pixelFormat: .depth32Float_stencil8,
  label: "Depth and Stencil Texture")
```

Here, you create the texture with the matching pixel format.

➤ In draw(commandBuffer:scene:uniforms:params:), after configuring the descriptor’s depth attachment, add:

```
descriptor?.stencilAttachment.texture = depthTexture
descriptor?.stencilAttachment.storeAction = .store
```

With this code, you tell the descriptor to use the depth texture as the stencil attachment and store the texture after use.

➤ Build and run the app, and choose the **Deferred** option.

<a id="page-397"></a>

➤ Capture the GPU workload and examine the command buffer.

![Figure](Metal_by_Tutorials_v500mpdf/db360b35ccb29451e0859ebb.png)

_New stencil texture_

Sure enough, you now have a stencil texture along with your other textures.

## Conﬁgure the Stencil Operation

➤ Open **GBufferRenderPass.swift**, and add this new method:

```
static func buildDepthStencilState() -> MTLDepthStencilState? {
  let descriptor = MTLDepthStencilDescriptor()
  descriptor.depthCompareFunction = .less
  descriptor.isDepthWriteEnabled = true
  return Renderer.device.makeDepthStencilState(
    descriptor: descriptor)
}
```

This is the same method to create a depth stencil state object in RenderPass, but you’ll override it with your stencil configuration.

<a id="page-398"></a>

➤ Add the following code to buildDepthStencilState() before return:

```
let frontFaceStencil = MTLStencilDescriptor()
frontFaceStencil.stencilCompareFunction = .always
frontFaceStencil.stencilFailureOperation = .keep
frontFaceStencil.depthFailureOperation = .keep
frontFaceStencil.depthStencilPassOperation = .incrementClamp
descriptor.frontFaceStencil = frontFaceStencil
```

frontFaceStencil affects the stencil buffer only for models’ faces facing the camera. The stencil test will always pass, and nothing happens if the stencil or depth tests fail. If the depth and stencil tests pass, the stencil buffer increases by 1.

➤ Build and run the app, and choose the **Deferred** option.

➤ Capture the GPU workload and select Command Buffer in the Debug navigator. Double click the stencil texture until you see the five attachments. When you move your cursor slowly across the stencil texture, you’ll see the value of the pixel. You can choose which attachments you want to view at the bottom of the panel.

![Figure](Metal_by_Tutorials_v500mpdf/5fe426d4fbf3e932667d87e5.png)

_The ground is rendered in front of the trees and sometimes fails the depth test_

Most of the texture is mid-gray with a value of 1. On the trees, which are mostly 1, there are small patches of 2, which incidentally uncovers some inefficient overlapping geometry in the tree model.

<a id="page-399"></a>

It’s important to realize that the geometry is processed in the order it’s rendered. In GameScene, this is set up as:

`models = [treefir1, treefir2, treefir3, train, ground]`

The ground is the last to render. It fails the depth test when the fragment is behind a tree or the train and doesn’t increment the stencil buffer.

Compare this with a stencil test where the ground is the first to render.

➤ Open GameScene.swift. In init(), change the models assignment to:

`models = [ground, treefir1, treefir2, treefir3, train]`

This code renders the ground first.

➤ Build and run the app, and choose the **Deferred** option.

➤ Capture the GPU workload and compare the stencil texture.

![Figure](Metal_by_Tutorials_v500mpdf/cc81667ee6bc8d77ab46035a.png)

_Ground renders first_

When the tree renders this time, the ground passing the depth test has already incremented the stencil buffer to 1, so the tree passes the depth test and increments the buffer to 2, then 3 when there is extra geometry.

You now have a stencil texture with zero where no geometry renders and non-zero where there is geometry.

All this aims to compute deferred lighting only in those areas with geometry. You can achieve this with your current stencil texture. Where the stencil buffer is zero, you can ignore the fragment in the light render pass.

<a id="page-400"></a>

To achieve this, you’ll:

1. Pass in the depth/stencil texture from GBufferRenderPass to LightingRenderPass.

2. In addition to setting LightingRenderPass‘s render pass descriptor’s stencil attachment, you must assign the depth texture to the descriptor’s depth attachment because you previously combine the stencil texture with depth.

3. LightingRenderPass uses two pipeline states: one for the sun and one for point lights. Both must have the depth and stencil pixel format of depth32float\_stencil.

## **1. Passing in the Depth/Stencil Texture**

➤ Open LightingRenderPass.swift, and add a new texture property to LightingRenderPass:

`weak var stencilTexture: MTLTexture?`

➤ Add this line to the top of draw(commandBuffer:scene:uniforms:params:):

`descriptor?.stencilAttachment.texture = stencilTexture`

➤ Open Renderer.swift. In draw(scene:in:), add this line where you assign the textures to lightingRenderPass:

```
lightingRenderPass.stencilTexture =
gBufferRenderPass.depthTexture
```

## **2. Setting Up the Render Pass Descriptor**

➤ Open LightingRenderPass.swift. At the top of draw(commandBuffer:scene:uniforms:params:), add:

```
descriptor?.depthAttachment.texture = stencilTexture
descriptor?.stencilAttachment.loadAction = .load
descriptor?.depthAttachment.loadAction = .dontCare
```

You set the stencil attachment to load so that the LightingRenderPass can use the stencil texture for stencil testing. You don’t need the depth texture, so you set a load action of dontCare.

<a id="page-401"></a>

## **3. Changing the Pipeline State Objects**

➤ Open Pipelines.swift.

In both createSunLightPSO(tiled:) and createPointLightPSO(tiled:), after pipelineDescriptor.depthAttachmentPixelFormat = Renderer.viewDepthPixelFormat, add:

```
if !tiled {
  pipelineDescriptor.depthAttachmentPixelFormat
    = .depth32Float_stencil8
  pipelineDescriptor.stencilAttachmentPixelFormat
    = .depth32Float_stencil8
}
```

This code configures the pipeline state to match the render pass descriptor’s depth and stencil texture pixel format.

➤ Build and run the app, and choose the **Deferred** option.

➤ Capture the GPU workload and examine the frame so far.

![Figure](Metal_by_Tutorials_v500mpdf/1c94e0f015be15061ae6e373.png)

_Stencil texture in frame capture_

LightingRenderPass correctly receives the stencil buffer from GBufferRenderPass.

<a id="page-402"></a>

## **Masking the Sky**

When you render the quad in LightingRenderPass, you want to bypass all fragments that are zero in the stencil buffer.

➤ Open LightingRenderPass.swift, and add this code to buildDepthStencilState() before return:

```
let frontFaceStencil = MTLStencilDescriptor()
frontFaceStencil.stencilCompareFunction = .equal
frontFaceStencil.stencilFailureOperation = .keep
frontFaceStencil.depthFailureOperation = .keep
frontFaceStencil.depthStencilPassOperation = .keep
descriptor.frontFaceStencil = frontFaceStencil
```

(Spoiler: Deliberate mistake!)

You haven’t changed the reference value in the render command encoder, so the reference value is zero. Here, you say that all stencil buffer fragments equal to zero will pass the stencil test. You don’t need to change the stencil buffer, so all of the operations are keep.

➤ Build and run the app, and choose the **Deferred** option.

![Figure](Metal_by_Tutorials_v500mpdf/4db70f25e581356e3f77b328.png)

_A deliberate mistake_

The GPU renders all fragments where the stencil fragment contains zero. That’s the top part. The bottom section with the plane and trees doesn’t render but shows the clear blue sky background. Of course, it should be the other way around.

<a id="page-403"></a>

➤ In `buildDepthStencilState()`, change the stencil compare function:

`frontFaceStencil.stencilCompareFunction = .notEqual`

➤ Build and run the app, then choose the **Deferred** option.

![Figure](Metal_by_Tutorials_v500mpdf/09417d529ccc5d4e435cd596.png)

_Clear blue skies_

At last, the brooding, stormy sky is replaced by the Metal view’s blue MTLClearColor that you set way back in Renderer’s initializer.

## **Challenge**

You fixed the sky for your Deferred Rendering pass. Your challenge is now to fix it in the Tiled Deferred render pass. Here’s a hint: just follow the steps for the Deferred render pass. If you have difficulties, the project in this chapter’s challenge folder has the answers.

<a id="page-404"></a>

## **Key Points**

• On Apple Silicon devices, keeping data in tile memory rather than transferring to system memory is much more efficient and uses less power.

• Mark textures as memoryless to keep them in tile memory.

• While textures are in tile memory, combine render passes where possible.

• Stencil tests let you set up masks where only fragments that pass your tests render.

• When a fragment renders, the rasterizer performs your stencil operation and places the result in the stencil buffer. With this stencil buffer, you control which parts of your image renders.

## **Where to Go From Here?**

Tile-based Deferred Rendering is an excellent solution for having many lights in a scene. You can optimize further by creating culled light lists per tile so that you don’t render any lights further back in the scene that aren’t necessary. Apple’s Modern Rendering with Metal 2019 video (https://apple.co/3mfdtEY) will help you understand how to do this. The video also points out when to use various rendering technologies.

<a id="page-405"></a>

# 16

# Chapter 16: GPU Compute Programming

General Purpose GPU (GPGPU) programming uses the many-core GPU architecture to speed up parallel computation. Data-parallel compute processing is useful when you have large chunks of data and need to perform the same operation on each chunk. Examples include machine learning, scientific simulations, ray tracing and image/video processing.

In this chapter, you’ll perform some simple GPU programming and explore how to use the GPU in ways other than vertex rendering.

<a id="page-406"></a>

## **The Starter Project**

➤ Open Xcode and build and run this chapter’s starter project.

The scene contains a lonely garden gnome. The renderer is a simplified forward renderer with no shadows.

![Figure](Metal_by_Tutorials_v500mpdf/04d1fae47a44c48cdfa8b28b.png)

_The starter project_

From this render, you might think that the gnome is holding the lamp in his left hand. Depending on how you render him, he can be ambidextrous.

➤ Press `1` on your keyboard.

The view changes to the front view. However, the gnome faces towards positive z instead of toward the camera.

![Figure](Metal_by_Tutorials_v500mpdf/a29b7cb8068dcc1a07411d28.png)

_Facing backwards_

<a id="page-407"></a>

The way the gnome renders is due to both math and file formats. In Chapter 6, “Coordinate Spaces”, you learned that this book uses a left-handed coordinate system. This USD file expects a right-handed coordinate system.

If you want a right-handed gnome, there are a few ways to solve this issue:

1. Rewrite all of your coordinate positioning.

2. In vertex\_main, invert position.z when rendering the model.

3. On loading the model, invert position.z.

If all of your models are reversed, option #1 or #2 might be good. However, if you only need some models reversed, option #3 is the way to go. All you need is a fast parallel operation. Thankfully, one is available to you using the GPU.

Note: Ideally, you would convert the model as part of your model pipeline rather than in your final app. After flipping the vertices, you can write the model out to a new file.

## **Winding Order and Culling**

Inverting the z position will flip the winding order of vertices, so you may need to consider this. When Model I/O reads in the model, the vertices are in clockwise winding order.

➤ To demonstrate this, open ForwardRenderPass.swift.

➤ In draw(commandBuffer:scene:uniforms:params:), add this code after renderEncoder.setRenderPipelineState(pipelineState):

```
renderEncoder.setFrontFacing(.counterClockwise)
renderEncoder.setCullMode(.back)
```

Here, you tell the GPU to expect vertices in counterclockwise order. The default is clockwise. You also tell the GPU to cull any faces that face away from the camera. As a general rule, you should cull back faces since they’re usually hidden, and rendering them isn’t necessary.

<a id="page-408"></a>

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/70e0111daeb564e0785e13b8.png)

_Rendering with incorrect winding order_

Because the winding order of the mesh is currently clockwise, the GPU is culling the wrong faces, and the model appears to be inside-out. Rotate the model to see this more clearly. Inverting the z coordinates will correct the winding order.

## **Reversing the Model on the CPU**

Before working out the parallel algorithm for the GPU, you’ll first explore how to reverse the gnome on the CPU. You’ll compare the performance with the GPU result. In the process, you’ll learn how to access and change Swift data buffer contents with pointers.

➤ In the Geometry folder, open VertexDescriptor.swift. Take a moment to refresh your memory about the layout in which Model I/O loads the model buffers in defaultLayout.

There are five vertex buffers that the vertex descriptor loads into four layouts. You’re currently only interested in the first vertex buffer layout, VertexBuffer. It consists of a float3 for Position and a float3 for Normal. You don’t need to consider UVs because they’re in the next layout.

➤ In the **Shaders** folder, open **Common.h**, and add a new structure:

```
struct VertexLayout {
  vector_float3 position;
  vector_float3 normal;
};
```

<a id="page-409"></a>

This structure matches the layout in the vertex descriptor for buffer 0. You’ll use it to read the loaded mesh buffer. Common.h is the bridging header, so you’ll be able to access anything you define here both in Swift and C++.

➤ In the Game folder, open GameScene.swift, and add a new method to GameScene:

```
mutating func convertMesh(_ model: Model) {
  let startTime = CFAbsoluteTimeGetCurrent()
  for mesh in model.meshes {
    // 1
    let vertexBuffer = mesh.vertexBuffers[VertexBuffer.index]
    let count =
      vertexBuffer.length / MemoryLayout<VertexLayout>.stride
    // 2
    var pointer = vertexBuffer
      .contents()
      .bindMemory(to: VertexLayout.self, capacity: count)
    // 3
    for _ in 0..<count {
      // 4
      pointer.pointee.position.z = -pointer.pointee.position.z
      // 5
      pointer = pointer.advanced(by: 1)
    }
  }
  // 6
  print("CPU Time:", CFAbsoluteTimeGetCurrent() - startTime)
}
```

Here’s a code breakdown:

1. First, you find the number of vertices in the vertex buffer. You calculate the number of vertices in the model by dividing the buffer length by the size of the vertex attribute layout. The result should match the number of vertices in the file. There are 15949 for the gnome.

2. vertexBuffer.contents() returns a MTLBuffer. You bind the buffer contents to pointer, making pointer an UnsafeMutablePointer&lt;VertexLayout&gt;.

3. You then iterate through each vertex.

4. The pointee is an instance of VertexLayout, and you invert the z position.

5. You then advance the pointer to the next vertex instance and continue.

6. Finally, you print out the time taken to do the operation.

<a id="page-410"></a>

Note: If you’re unfamiliar with Swift pointers, read our article Unsafe Swift: Using Pointers and Interacting With C (https://www.kodeco.com/7181017- unsafe-swift-using-pointers-and-interacting-with-c).

➤ Add this code to the end of `init()` to call the new method:

`convertMesh(gnome)`

➤ Build and run the app and press **1** for the front view.

![Figure](Metal_by_Tutorials_v500mpdf/3508786d11a5234d608ca48f.png)

_A right-handed gnome_

The gnome is now right-handed. On the M1 MacBook Pro, the time taken was 0.00215. That’s pretty fast, but the gnome is a small model with only sixteen thousand vertices.

Look for operations you could possibly do in parallel and process with a GPU kernel. Within the for loop, you perform the same operation on every vertex independently, so it’s a good candidate for GPU compute. Independently is the critical word, as GPU threads perform operations independently from each other.

## **Compute Processing**

In many ways, compute processing is similar to the render pipeline. You set up a command queue and a command buffer. In place of the render command encoder, compute uses a compute command encoder. Instead of using vertex or fragment functions in a compute pass, you use a kernel function. Threads are the input to the kernel function, and the kernel function operates on each thread.

<a id="page-411"></a>

## **Threads and Threadgroups**

To determine how many times you want the kernel function to run, you need to know the size of the array, texture or volume you want to process. This size is the grid and consists of threads organized into threadgroups.

The grid is defined in three dimensions: width, height and depth. But often, especially when you’re processing images, you’ll only work with a 1D or 2D grid. Every point in the grid runs one instance of the kernel function, each on a separate thread.

➤ Look at the following example image:

![Figure](Metal_by_Tutorials_v500mpdf/b0a716a34bfb9238a33e6e52.png)

_Threads and threadgroups_

The image is 512×384 pixels. You need to tell the GPU the number of threads per grid and the number of threads per threadgroup.

Threads per grid: In this example, the grid is two dimensions, and the number of threads per grid is the image size of 512 by 384.

Threads per threadgroup: Specific to the device, the pipeline state’s threadExecutionWidth suggests the best width for performance, and maxTotalThreadsPerThreadgroup specifies the maximum number of threads in a threadgroup. On a device with 512 as the maximum number of threads, and a thread execution width of 32, the optimal 2d threadgroup size would have a width of 32 and a height of 512 / 32 = 16. So the threads per threadgroup will be 32 by 16.

<a id="page-412"></a>

In this case, the compute dispatch code looks something like this:

```
let threadsPerGrid = MTLSize(width: 512, height: 384, depth: 1)
let width = pipelineState.threadExecutionWidth
let threadsPerThreadgroup = MTLSize(
  width: width,
  height: pipelineState.maxTotalThreadsPerThreadgroup / width,
  depth: 1)
computeEncoder.dispatchThreads(
  threadsPerGrid,
  threadsPerThreadgroup: threadsPerThreadgroup)
```

You specify the threads per grid and let the pipeline state work out the optimal threads per threadgroup.

## **Non-uniform Threadgroups**

The threads and threadgroups work out evenly across the grid in the previous image example. However, if the grid size isn’t a multiple of the threadgroup size, Metal provides non-uniform threadgroups.

![Figure](Metal_by_Tutorials_v500mpdf/437c93abb76ad051a94542bd.png)

_Non-uniform threadgroups_

## **Threadgroups per Grid**

You can choose how you split up the grid. Threadgroups have the advantage of executing a group of threads together and also sharing a small chunk of memory. It’s common to organize threads into threadgroups to work on smaller parts of the problem independently from other threadgroups.

<a id="page-413"></a>

In the following image, a 16 by 12 grid is split first into 2✕3 threadgroups and then into 4✕4 thread groups.

![Figure](Metal_by_Tutorials_v500mpdf/9694887f878613c9805f515f.png)

_Threadgroups in a 2D grid_

In the kernel function, you can locate each pixel in the grid. The red pixel in both grids is located at (11, 1).

You can also uniquely identify each thread within the threadgroup. The blue threadgroup on the left is located at (1, 0) and on the right at (2, 0). The red pixels in both grids are threads located within their own threadgroup at (3, 1).

You have control over the number of threadgroups. However, you need to add an extra threadgroup to the size of the grid to make sure at least one threadgroup executes.

Using the cat image example, you could choose to set up the threadgroups in the compute dispatch like this:

```
let width = 32
let height = 16
let threadsPerThreadgroup = MTLSize(
  width: width, height: height, depth: 1)
let gridWidth = 512
let gridHeight = 384
let threadGroupCount = MTLSize(
  width: (gridWidth + width - 1) / width,
  height: (gridHeight + height - 1) / height,
  depth: 1)
computeEncoder.dispatchThreadgroups(
  threadGroupCount,
  threadsPerThreadgroup: threadsPerThreadgroup)
```

You specify the threads per threadgroup. In this case, the threadgroup will consist of 32 threads wide, 16 threads high and 1 thread deep.

If the size of your data does not match the size of the grid, you may have to perform boundary checks in the kernel function.

<a id="page-414"></a>

In the following example, with a threadgroup size of 32 by 16 threads, the number of threadgroups necessary to process the image would be 10 by 13. You’d have to check that the threadgroup isn’t using threads that are off the edge of the image.

![Figure](Metal_by_Tutorials_v500mpdf/6b78f598fa7ad5f72d53e8bd.png)

_Underutilized threads_

The threads that are off the edge are underutilized. That is, they’re threads that you dispatched, but there was no work for them to do.

## Reversing the Gnome Using GPU Compute Processing

The previous example was a two-dimensional image, but you can create grids in one, two or three dimensions. The gnome problem acts on an array in a buffer and will require a one-dimensional grid.

➤ In the Geometry folder, open Model.swift, and add a new method to Model:

```
func convertMesh() {
// 1
  guard let commandBuffer =
    Renderer.commandQueue.makeCommandBuffer(),
    let computeEncoder =
commandBuffer.makeComputeCommandEncoder()
      else { return }
  // 2
  let startTime = CFAbsoluteTimeGetCurrent()
  // 3
  let pipelineState: MTLComputePipelineState
  do {
    // 4
    guard let kernelFunction =
      Renderer.library.makeFunction(name: "convert_mesh") else {
        fatalError("Failed to create kernel function")
      }
```

<a id="page-415"></a>

```
    // 5
    pipelineState = try
      Renderer.device.makeComputePipelineState(
        function: kernelFunction)
  } catch {
    fatalError(error.localizedDescription)
  }
  computeEncoder.setComputePipelineState(pipelineState)
}
```

Going through the code:

1. You create the compute command encoder the same way you created the render command encoder.

2. You add a start time to see how long the conversion takes to execute.

3. For compute processing, you use a compute pipeline state. This requires fewer state changes on the GPU, so you don’t need a descriptor.

4. Soon, you’ll create the kernel function convert\_mesh.

5. Finally, you create the pipeline state using the kernel function. You then set the GPU pipeline state in the compute encoder.

➤ Continue by adding the following code to the end of convertMesh():

```
for mesh in meshes {
  let vertexBuffer = mesh.vertexBuffers[VertexBuffer.index]
  computeEncoder.setBuffer(vertexBuffer, offset: 0, index: 0)
  let vertexCount = vertexBuffer.length /
    MemoryLayout<VertexLayout>.stride
}
```

Just as you did in the earlier CPU version, you calculate the vertex count, which is the number of threads required.

## **Setting up Threadgroups**

➤ Within the previous `for` loop closure, continue with:

```
let threadsPerGroup = MTLSize(
  width: pipelineState.threadExecutionWidth,
  height: 1,
  depth: 1)
let threadsPerGrid = MTLSize(width: vertexCount, height: 1,
depth: 1)
computeEncoder.dispatchThreads(
```

<a id="page-416"></a>

```
  threadsPerGrid,
  threadsPerThreadgroup: threadsPerGroup)
computeEncoder.endEncoding()
```

You set up the grid and threadgroup the same way as the initial image example. Since your model’s vertices are a one-dimensional array, you only set up width. Then, you extract the device-dependent thread execution width from the pipeline state to get the number of threads in a thread group. The grid size is the number of vertices in the model.

The dispatch call is the compute command encoder’s equivalent to the render command encoder’s draw call. The GPU will execute the kernel function specified in the pipeline state when you commit the command buffer.

## Performing Code After Completing GPU Execution

The command buffer can execute a closure after its GPU operations have finished.

➤ Outside the for loop, add this code at the end of convert\_mesh():

```
commandBuffer.addCompletedHandler { _ in
  print(
    "GPU conversion time:",
    CFAbsoluteTimeGetCurrent() - startTime)
}
commandBuffer.commit()
```

You supply a closure that calculates the amount of time the procedure takes and print it out. You then commit the command buffer to the GPU.

## **The Kernel Function**

That completes the Swift setup. You simply specify the kernel function to the pipeline state and create an encoder using that pipeline state. With that, it’s only necessary to give the thread information to the encoder. The rest of the action takes place inside the kernel function.

<a id="page-417"></a>

➤ In the Shaders folder, create a new Metal file named ConvertMesh.metal, and add:

```
#import "Common.h"

kernel void convert_mesh(
  device VertexLayout *vertices [[buffer(0)]],
  uint id [[thread_position_in_grid]])
{
  vertices[id].position.z = -vertices[id].position.z;
}
```

A kernel function can’t have a return value. Using the thread\_position\_in\_grid attribute, you pass in the vertex buffer and identify the thread ID using the thread\_position\_in\_grid attribute. You then invert the vertex’s z position.

This function will execute for every vertex in the model.

➤ Open GameScene.swift. In init(), replace convertMesh(gnome) with:

`gnome.convertMesh()`

➤ Build and run the app. Press the `1` key for the front view of the model.

![Figure](Metal_by_Tutorials_v500mpdf/e53f0c5d31ac784e0dd10011.png)

_A right-handed gnome_

The console prints out the time of GPU processing. You’ve had your first experience with data-parallel processing, and the gnome is now right-handed and faces toward the camera.

<a id="page-418"></a>

Compare the time with the CPU conversion. On my M1 MacBook Pro, the GPU conversion time is 0.00145. Always check the comparative times, as setting up a GPU pipeline is a time cost. It may take less time to perform the operation on the CPU on small operations.

## **Atomic Functions**

Kernel functions perform operations on individual threads. However, you may want to perform an operation that requires information from other threads. For example, you might want to find out the total number of vertices your kernel worked on.

Your kernel function operates on each thread independently, and these threads update each vertex position simultaneously. If you send the kernel function a variable to store the total in a buffer, the function can increment the total, but other threads will be doing the same thing simultaneously. Therefore you won’t get the correct total.

An **atomic operation** works in shared memory and is visible to other threads.

➤ Open Model.swift. In convertMesh(), add the following code before for mesh in meshes:

```
let totalBuffer = Renderer.device.makeBuffer(
  length: MemoryLayout<Int>.stride,
  options: [])
let vertexTotal = totalBuffer?.contents().bindMemory(to:
Int.self, capacity: 1)
vertexTotal?.pointee = 0
computeEncoder.setBuffer(totalBuffer, offset: 0, index: 1)
```

Here, you create a buffer to hold the total number of vertices. You bind the buffer to a pointer and set the contents to zero. You then send the buffer to the GPU.

➤ Still in convertMesh(), add this code to the command buffer’s completion handler:

`print("Total Vertices:", vertexTotal?.pointee ?? -1)`

You print out the contents of the buffer, which contains the total number of vertices.

➤ Open ConvertMesh.metal and add this code to convert\_mesh’s parameters:

`device int &vertexTotal [[buffer(1)]],`

<a id="page-419"></a>

➤ Then, add this code to the end of the function:

`vertexTotal++;`

You add one to `vertexTotal` each time the function executes.

➤ Build and run the app. Check the debug console output.

GPU conversion time: 0.0012869834899902344 Total Vertices: 2

Each time you run the app, you’ll get a different incorrect result depending on how the GPU scheduled the threads. The threads add one to the buffer at precisely the same time before the buffer can store the values from the other threads.

➤ Still in **ConvertMesh.metal**, change the `vertexTotal` parameter to:

`device atomic_int &vertexTotal [[buffer(1)]],`

Instead of an int, you define an atomic\_int, telling the GPU that this will work in shared memory.

➤ Replace `vertexTotal++` with:

```
atomic_fetch_add_explicit(&vertexTotal, 1,
memory_order_relaxed);
```

Since you can’t do simple operations on the atomic variable anymore, you call the built-in function that takes in vertexTotal as the first parameter and the amount to add as the second parameter.

➤ Build and run the app.

Now the correct number of vertices prints out in the debug console.

GPU conversion time: 0.0013600587844848633 Total Vertices: 15949

There are various atomic functions, and you can find out more about them in Chapter 6.15.4, “Atomic Functions” in Apple’s Metal Shading Language Specification (https://apple.co/3zLTwve)

With this simple introduction to compute shaders, you’re ready for the next few chapters, where you’ll create stunning particle effects and even control some strange creatures called boids.

<a id="page-420"></a>

## **Key Points**

• GPU compute, or general purpose GPU programming, helps you perform data operations in parallel without using the more specialized rendering pipeline.

• You can move any task that operates on multiple items independently to the GPU. Later, you’ll see that you can even move the repetitive task of rendering a scene to a compute shader.

• GPU memory is good at simple parallel operations, and with Apple silicon, you can keep chained operations in tile memory instead of moving them back to system memory.

• Compute processing uses a compute pipeline with a kernel function.

• The kernel function operates on a grid of threads organized into threadgroups. This grid can be 1D, 2D or 3D.

• Atomic functions allow inter-thread operations.

<a id="page-421"></a>

# 17

# Chapter 17: Particle Systems

One of the many ways to create art and present science in code is by making use of particles. A particle is a tiny graphical object that carries basic information about itself such as color, position, life, speed and direction of movement.

Nothing explains a visual effect better than an image showing what you’ll be able to achieve at the end of this chapter:

![Figure](Metal_by_Tutorials_v500mpdf/5b7394343accfb6dd81ac91c.png)

_Particle systems_

Particle systems are widely used in:

• Video games and animation: hair, cloth, fur.

• Modeling of natural phenomena: fire, smoke, water, snow.

• Scientific simulations: galaxy collisions, cellular mitosis, fluid turbulence.

<a id="page-422"></a>

Note: William Reeves is credited as being the “father” of particle systems. While at Lucasfilm, Reeves created the Genesis Effect in 1982 while working on the movie Star Trek II: The Wrath of Khan. Later, he joined Pixar Animation Studios where he’s still creating amazing animations using particles.

In a moment, you’ll get your feet wet trying out one such practical application: fireworks. But first, what exactly is a particle?

## **Particle**

Newtonian dynamics describe the relationship between any small body — a particle — and the forces acting upon it, as well as its motion in response to those forces. Newton’s three laws of motion define the relationship between them. The first two laws define motion as a result of either inertia or force interference upon the particle’s current state of motion (stationary or moving). You’ll be working with them in this chapter. The third law, however, defines motion as a reaction of two or more particles interacting with each other. You’ll work with this law in Chapter 18, “Particle Behavior”.

A fourth law, if you wish, is the law of life. It’s not one of the Newtonian motion laws, but it does indeed apply to particles. Particles are born. They move and interact with the environment, and then they die.

![Figure](Metal_by_Tutorials_v500mpdf/901cfb46e7210ce042dd08ec.png)

_Particle life_

You need a particle system to create fireworks. But first, you need to define a particle that has — at a minimum — a position, direction, speed, color and life. What makes a particle system cohesive, though, are emitters.

<a id="page-423"></a>

## **Emitter**

An emitter is nothing more than a particle generator — in other words, a source of particles. You can make your particle system more exciting by having several emitters shooting out particles from different positions.

Fireworks are sequential explosions that occur a few seconds apart from each other, so you will create several emitters.

## **The Starter Project**

➤ In Xcode, open the starter project for this chapter, then build and run it.

![Figure](Metal_by_Tutorials_v500mpdf/ad368916f0237520edaccb83.png)

_The starter project_

The project contains an empty scene, rendering with the forward renderer that you’re already familiar with. The dark blue color comes from setting metalView.clearColor in Renderer.init(metalView:options:).

• The Particles folder contains two files that you’ll use later in the chapter.

• The Fireworks folder, inside the Particles folder, is where you’ll create your first particle system.

• In the Textures folder, Textures.xcassets contains two sprite textures that you’ll attach to particle systems.

• Renderer is already set up with skeleton structures to render fireworks and particles.

• PipelineStates contains a factory method to create a particle render pipeline state.

<a id="page-424"></a>

## **Creating a Particle and Emitter**

➤ In the **Shaders** folder, open **Common.h**, and add a new structure:

```
struct Particle {
  vector_float2 position;
  float direction;
  float speed;
  vector_float4 color;
  float life;
};
```

This structure holds the properties for each particle.

➤ In the Particles/Fireworks folder, create a new Swift file called FireworksEmitter.swift, and replace the code with this:

```
import MetalKit

struct FireworksEmitter {
  let particleBuffer: MTLBuffer

  init(
    particleCount: Int,
    size: CGSize,
    life: Float
  ) {
    let bufferSize =
      MemoryLayout<Particle>.stride * particleCount
    particleBuffer =
      Renderer.device.makeBuffer(length: bufferSize)!
  }
}
```

This code takes in the particle count and the particle’s lifetime. You then create the buffer that will hold all the particle data.

You’ll randomize the initial position and color once for all particles, and then randomize each particle’s speed and direction based on the size of the display area.

➤ Add the following code to init(particleCount:size:life:):

```
let width = Float(size.width)
let height = Float(size.height)
let position = float2(
  Float.random(in: 0...width),
  Float.random(in: 0...height))
let color = float4(
  Float.random(in: 0...life) / life,
```

<a id="page-425"></a>

```
  Float.random(in: 0...life) / life,
  Float.random(in: 0...life) / life,
  1)
```

You set up initial properties for the emitter. Each firework emitter will have a random position where all the particles will start. All particles will have the same random color.

➤ Continue adding the following code after the code you just added:

```
var pointer =
  particleBuffer.contents().bindMemory(
    to: Particle.self,
    capacity: particleCount)
for _ in 0..<particleCount {
  let direction = Float.random(in: 0...(2 * Float.pi))
  let speed = Float.random(in: 0...3)
  pointer.pointee.position = position
  pointer.pointee.direction = direction
  pointer.pointee.speed = speed
  pointer.pointee.color = color
  pointer.pointee.life = life
  pointer = pointer.advanced(by: 1)
}
```

Here, you loop through the buffer using a pointer to access each particle object and set their properties.

You’ve now created lots of particles, each with distinct direction and speed. All of them have the same original position, color and life.

➤ In the Fireworks folder, open Fireworks.swift.

This file contains two methods that you’ll fill out shortly. Renderer calls these on each frame.

➤ Add these properties to Fireworks:

```
let particleCount = 10000
let maxEmitters = 8
var emitters: [FireworksEmitter] = []
let life: Float = 256
var timer: Float = 0
```

You’ll set up an array of emitters, each with 10,000 particles.

<a id="page-426"></a>

➤ Add this code to update(size:):

```
timer += 1
if timer >= 50 {
  timer = 0
  if emitters.count > maxEmitters {
    emitters.removeFirst()
  }
  let emitter = FireworksEmitter(
    particleCount: particleCount,
    size: size,
    life: life)
  emitters.append(emitter)
}
```

You reset a timer variable every time it reaches a threshold (50 in this case). At that point, you add a new emitter and then remove the oldest one.

➤ Build and run the app to verify everything is working. Note, however, you’ll see the same solid dark blue color as you did in the beginning as you’re not doing any drawing yet.

The shader function is where you’ll update the particles’ life and position. Each of the particles is updated independently, and so will work well with the granular control of GPU threads in compute encoding!

## **The Compute Pipeline State Object**

➤ In the Render Passes folder, open Pipelines.swift and add this to PipelineStates:

```
static func createComputePSO(function: String)
  -> MTLComputePipelineState {
  guard let kernel = Renderer.library.makeFunction(name:
function)
  else { fatalError("Unable to create \(function) PSO") }
  let pipelineState: MTLComputePipelineState
  do {
    pipelineState =
    try Renderer.device.makeComputePipelineState(function:
kernel)
  } catch {
    fatalError(error.localizedDescription)
  }
  return pipelineState
}
```

<a id="page-427"></a>

As you learned in the previous chapter, for a compute pipeline state, you don’t need a pipeline state descriptor. You simply create the pipeline state directly from the kernel function. You’ll be able to use this method to create compute pipeline state objects using only the name of the kernel.

## **The Fireworks Pass**

➤ Open **Fireworks.swift**, and add the pipeline states and initializer:

```
let clearScreenPSO: MTLComputePipelineState
let fireworksPSO: MTLComputePipelineState

init() {
  clearScreenPSO =
    PipelineStates.createComputePSO(function: "clearScreen")
  fireworksPSO =
    PipelineStates.createComputePSO(function: "fireworks")
}
```

When you display your particles on the screen, you’ll write them to the drawable texture. Because you’re not going through the render pipeline, you will need to clear the texture to a night sky black. You’ll do this in a simple compute shader.

Note: In this particular application, because you’re using the drawable texture, you could set the initial metal view’s clear color to black instead of running a clear screen kernel function. But clearing the drawable texture will give you practice in using a 2D grid, and the skill to clear other textures too.

After clearing the screen, you’ll then be able to calculate the fireworks particles.

You will require a different kernel function for each process, requiring two different pipeline state objects.

<a id="page-428"></a>

## **Clearing the Screen**

The clear screen kernel function will run on every pixel in the drawable texture. The texture has a width and height, and is therefore a two dimensional grid.

➤ Still in Fireworks.swift, add this to draw(commandBuffer:view:):

```
// 1
guard let computeEncoder =
commandBuffer.makeComputeCommandEncoder(),
  let drawable = view.currentDrawable
  else { return }
computeEncoder.setComputePipelineState(clearScreenPSO)
computeEncoder.setTexture(drawable.texture, index: 0)
// 2
var threadsPerGrid = MTLSize(
  width: Int(view.drawableSize.width),
  height: Int(view.drawableSize.height),
  depth: 1)
// 3
let width = clearScreenPSO.threadExecutionWidth
var threadsPerThreadgroup = MTLSize(
  width: width,
  height: clearScreenPSO.maxTotalThreadsPerThreadgroup / width,
  depth: 1)
// 4
computeEncoder.dispatchThreads(
  threadsPerGrid,
  threadsPerThreadgroup: threadsPerThreadgroup)
computeEncoder.endEncoding()
```

Going through the code:

1. You create the compute command encoder and set its pipeline state. You also send the drawable texture to the GPU at index 0 for writing.

2. The grid size is the drawable’s width by the drawable’s height.

3. Using the pipeline state thread values, you calculate the number of threads per threadgroup.

4. You dispatch these threads to do the work in parallel on the GPU.

➤ In the Shaders folder, create a new Metal file named Fireworks.metal, and add the kernel functions you set up in your pipeline states:

```
#import "Common.h"

kernel void clearScreen(
```

<a id="page-429"></a>

```
  texture2d<half, access::write> output [[texture(0)]],
  uint2 id [[thread_position_in_grid]])
{
  output.write(half4(0.0, 0.0, 0.0, 1.0), id);
}

kernel void fireworks()
{ }
```

clearScreen takes, as arguments, the drawable texture you sent from the CPU and the 2D thread index. You specify in the parameter that you will need write access. Then, you write the color black into the drawable texture for each thread/pixel.

The kernel function’s id parameter uses the [[thread\_position\_in\_grid]] attribute qualifier which uniquely locates a thread within the compute grid and enables it to work distinctly from the others. In this case, it identifies each pixel in the texture.

You’ll return and fill out `fireworks` shortly.

➤ Open Renderer.swift, and add this at the end of init(metalView:options:):

`metalView.framebufferOnly = false`

Because you’re writing to the view’s drawable texture in clearScreen, you need to change the underlying render target usage by enabling writing to the frame buffer.

➤ Take a look at draw(scene:in:).

Renderer is already set up to call fireworks(update:size:) and fireworks.draw(commandBuffer:view:).

➤ Build and run the app.

clearScreen writes the color to the view’s drawable texture, so you’ll finally see the view color turns from blue to a night sky ready to display your fireworks.

![Figure](Metal_by_Tutorials_v500mpdf/0c4a62733e97e877d00329cf.png)

_Drawable cleared to black_

<a id="page-430"></a>

## **Dispatching the Particle Buffer**

Now that you’ve cleared the screen, you’ll set up a new encoder to dispatch the particle buffer to the GPU.

➤ Open Fireworks.swift, and add this to the end of draw(commandBuffer:view:):

```
// 1
guard let particleEncoder =
commandBuffer.makeComputeCommandEncoder()
  else { return }
particleEncoder.setComputePipelineState(fireworksPSO)
particleEncoder.setTexture(drawable.texture, index: 0)
// 2
threadsPerGrid = MTLSize(width: particleCount, height: 1, depth:
1)
for emitter in emitters {
  // 3
  let particleBuffer = emitter.particleBuffer
  particleEncoder.setBuffer(particleBuffer, offset: 0, index: 0)
  threadsPerThreadgroup = MTLSize(
    width: fireworksPSO.threadExecutionWidth,
    height: 1,
    depth: 1)
  particleEncoder.dispatchThreads(
    threadsPerGrid,
    threadsPerThreadgroup: threadsPerThreadgroup)
}
particleEncoder.endEncoding()
```

This code is similar to the previous compute encoder setup:

1. You create a second command encoder and set the particle pipeline state and drawable texture to it.

2. You change the dimensionality from 2D to 1D and set the number of threads per grid to equal the number of particles.

3. You dispatch threads for each emitter in the array.

Since your threadsPerGrid is now 1D, you’ll need to match [[thread\_position\_in\_grid]] in the shader kernel function with a uint parameter. Threads will not be dispatched for each pixel anymore but rather for each particle, so [[thread\_position\_in\_grid]] in this case will only affect a particular pixel in the drawable texture if there is a particle positioned at that pixel.

All right, time for some physics chatter!

<a id="page-431"></a>

## **Particle Dynamics**

Particle dynamics makes heavy use of Newton’s laws of motion. Particles are considered to be small objects approximated as point masses. Since volume is not something that characterizes particles, scaling or rotational motion will not be considered. Particles will, however, make use of translation motion so they’ll always need to have a position.

In addition to its position, particles might also have a direction and speed of movement (velocity), forces that influence them (e.g., gravity), a mass, a color and an age. Since the particle footprint is so small in memory, modern GPUs can generate 4+ million particles, and they can follow the laws of motion at 60 fps.

For now, you’re going to ignore gravity, so its value will be 0. Time in this example won’t change so it will have a value of 1. As a consequence, velocity will always be the same. You can also assume the particle mass is always 1, for convenience.

To calculate the position, you use this formula:

![Figure](Metal_by_Tutorials_v500mpdf/4d80a774b3fd93c58bbbf94b.png)

Where x2 is the new position, x1 is the old position, v1 is the old velocity, t is time, and a is acceleration.

This is the formula to calculate the new velocity from the old one:

![Figure](Metal_by_Tutorials_v500mpdf/a95541981750c83a1b40a499.png)

However, since the acceleration is 0 in the fireworks example, the velocity will always have the same value.

As you might remember from Physics class, the formula for velocity is:

`velocity = speed * direction`

Plugging all this information into the first formula above gives you the final equation to use in the kernel.

Again, as for the second formula, since acceleration is `0`, the last term cancels out:

`newPosition = oldPosition * velocity`

<a id="page-432"></a>

Finally, you’re creating exploding fireworks, so your firework particles will move in a circle that keeps growing away from the initial emitter origin, so you need to know the equation of a circle:

![Figure](Metal_by_Tutorials_v500mpdf/5af52173701c4f89ca16144e.png)

Using the angle that the particle direction makes with the axes, you can re-write the velocity equation from the parametric form of the circle equation using the trigonometric functions sine and cosine as follows:

```
xVelocity = speed * cos(direction)
yVelocity = speed * sin(direction)
```

Great! Let’s write all of this in code.

## **Implementing Particle Physics**

➤ Open **Fireworks.metal** and replace `fireworks` with:

```
kernel void fireworks(
  texture2d<half, access::write> output [[texture(0)]],
  // 1
  device Particle *particles [[buffer(0)]],
  uint id [[thread_position_in_grid]]) {
  // 2
  float xVelocity = particles[id].speed
    * cos(particles[id].direction);
  float yVelocity = particles[id].speed
    * sin(particles[id].direction) + 3.0;
  particles[id].position.x += xVelocity;
  particles[id].position.y += yVelocity;
  // 3
  particles[id].life -= 1.0;
  half4 color;
  color = half4(particles[id].color) * particles[id].life /
255.0;
  // 4
  color.a = 1.0;
  uint2 position = uint2(particles[id].position);
  output.write(color, position);
  output.write(color, position + uint2(0, 1));
  output.write(color, position - uint2(0, 1));
  output.write(color, position + uint2(1, 0));
  output.write(color, position - uint2(1, 0));
}
```

<a id="page-433"></a>

Going through this code:

1. Get the particle buffer from the CPU and use a 1D index to match the grid dimensions you dispatched earlier.

2. Compute the velocity and update the position for the current particle according to the laws of motion and using the circle equation as explained above.

3. Update the life variable and compute a new color after each update. The color will fade as the value held by the life variable gets smaller and smaller.

4. Write the updated color at the current particle position, as well as its neighboring particles to the left, right, top and bottom to create the look and feel of a thicker particle.

➤ Build and run the app, and finally you get to enjoy some fireworks!

![Figure](Metal_by_Tutorials_v500mpdf/ccf795bffe2ec84f7447fdab.png)

_Fireworks!_

You can improve the realism of particle effects in a couple of ways. One of them is to attach a sprite or a texture to each particle in a render pass. Instead of a dull point, you’ll then be able to see a textured point which looks way more lively.

You can practice this technique in your next particle endeavor: a snowing simulation.

## **Particle Systems**

The fireworks particle system was tailor-made for fireworks. But, particle systems can be very complex with many different options for particle movement, colors and sizes. In the Particles folder, the Emitter class in the starter project is a simple example of a generic particle system where you can create many different types of

<a id="page-434"></a>

particles using a particle descriptor.

For example, you’re going to create snow falling, but also a fire blazing upwards. These particle systems will have different speeds, textures and directions.

➤ In the Particles folder, open ParticleEffects.swift, and examine the ParticleDescriptor structure.

To create a particle system, you first create a descriptor which describes all the characteristics of each individual particle.

Many of the properties in ParticleDescriptor are ClosedRanges. For example, as well as position, there is a positionXRange and positionYRange. This allows you to specify a starting position but also allows randomness within limits. If you specify a position of [10, 0], and a positionXRange of 0...180, then each particle will be within the range of 10 to 190.

Each particle has a startScale and an endScale. By setting the startScale to 1 and the endScale to 0, you can make the particle get smaller over its lifespan.

![Figure](Metal_by_Tutorials_v500mpdf/d1f6c66108ff4f622c8538cc.png)

_Scaling over time_

➤ Open Emitter.swift.

When you create the emitter, you’ll specify the particle descriptor along with these properties:

• texture: You’ll render this texture for each particle using the particle coordinates.

• particleCount: The total number of particles.

• birthRate: How many particles should generate at one time.

<a id="page-435"></a>

• birthDelay: Delays particle generation. This allows you to slowly release particles (like a gentle snow flurry) or send them out more quickly (like a blazing fire).

• blending: Some particle effects require blending, such as you did for your point lights in Chapter 14, “Deferred Rendering”.

Emitter creates a buffer the size of all the particles. emit() processes each new particle and creates it with the particle settings you set up in the particle descriptor.

More complex particle systems would maintain a live buffer and a dead buffer. As particles die, they move from live to dead, and as the system requires new particles, it recovers them from dead. However, in this more simple system, a particle never dies. As soon as a particle’s age reaches its life-span, it’s reborn with the values it started with.

## **Resetting the Scene**

To add this new, more generic particle system, remove your fireworks simulation from Renderer.

➤ Open **Renderer.swift** and remove:

`var fireworks: Fireworks`

➤ In `init(metalView:options:)`, remove:

`fireworks = Fireworks()`

➤ In `draw(scene:in:)`, remove:

```
// Render Fireworks with compute shaders
fireworks.update(size: view.drawableSize)
fireworks.draw(commandBuffer: commandBuffer, view: view)
```

➤ Build and run the app, and your screen will show the metal view’s initial clear color.

![Figure](Metal_by_Tutorials_v500mpdf/88950ecb1608dc424c8e2e55.png)

_Reset project_

<a id="page-436"></a>

Your game may require many different particle effects, so you’ll add them to the game scene.

➤ Open GameScene.swift, and add a new property to GameScene:

`var particleEffects: [Emitter] = []`

Each particle effect will be an emitter, which you’ll add to this array.

## **Updating the Particle Structure**

With a more complex particle system, you need to store more particle properties.

➤ Open Common.h, and add this to the end of Particle:

```
float age;
float size;
float scale;
float startScale;
float endScale;
vector_float2 startPosition;
```

You’ll now be able to decay the size of the particle over time.

➤ Open Emitter.swift and remove the Particle structure. Emitter will now use the structure in Common.h.

## **Rendering a Particle System**

You’ll attach a texture to snow particles to improve the realism of your rendering. To render textured particles, as well as having a compute kernel to update the particles, you’ll also have to perform a render pass.

➤ In the Render Passes folder, open ParticlesRenderPass.swift.

This is a skeleton render pass with the minimum requirements to conform to RenderPass. It’s already set up to render in Renderer.

draw(commandBuffer:scene:uniforms:params:) first calls update(commandBuffer:scene:). This is where you’ll first create the compute pipeline to update the particles. You’ll then build the pipeline for rendering the particles in render(commandBuffer:scene:).

<a id="page-437"></a>

➤ In ParticlesRenderPass, create the necessary pipeline state properties and replace init(view:):

```
let computePSO: MTLComputePipelineState
let renderPSO: MTLRenderPipelineState
let blendingPSO: MTLRenderPipelineState

init(view: MTKView) {
  computePSO = PipelineStates.createComputePSO(
    function: "computeParticles")
  renderPSO = PipelineStates.createParticleRenderPSO()
  blendingPSO = PipelineStates.createParticleRenderPSO(
    enableBlending: true)
}
```

computeParticles is the kernel function where you’ll update the particles every frame.

The two render pipeline states will use the vertex function vertex\_particle to position a point on the screen, and fragment\_particle to draw the sprite texture into the point.

➤ Add this code to update(commandBuffer:scene:):

```
// 1
guard let computeEncoder =
  commandBuffer.makeComputeCommandEncoder() else { return }
computeEncoder.label = label
computeEncoder.setComputePipelineState(computePSO)
// 2
let threadsPerGroup = MTLSize(
  width: computePSO.threadExecutionWidth, height: 1, depth: 1)
// 3
for emitter in scene.particleEffects {
  emitter.emit()
  if emitter.currentParticles <= 0 { continue }
  // 4
  let threadsPerGrid = MTLSize(
    width: emitter.particleCount, height: 1, depth: 1)
  computeEncoder.setBuffer(
    emitter.particleBuffer,
    offset: 0,
    index: 0)
  computeEncoder.dispatchThreads(
    threadsPerGrid,
    threadsPerThreadgroup: threadsPerGroup)
}
computeEncoder.endEncoding()
```

<a id="page-438"></a>

Going through the code:

1. You create the compute command encoder and set the pipeline state.

2. You use the pipeline state’s default thread execution width.

3. You process each emitter in the scene.

4. The 1D grid is the number of particles in the emitter.

Note: The previous code, which may create non-uniform threadgroup sizes, will only work on macOS, and iOS devices included in Apple 4 and later GPUs. In addition, Simulator does not support non-uniform threadgroup sizes.

➤ Add this code to render(commandBuffer:scene:):

```
guard let descriptor = descriptor,
  let renderEncoder =
    commandBuffer.makeRenderCommandEncoder(descriptor:
descriptor)
  else { return }
renderEncoder.label = label
var size: float2 = [Float(size.width), Float(size.height)]
renderEncoder.setVertexBytes(
  &size,
  length: MemoryLayout<float2>.stride,
  index: 0)
```

render(commandBuffer:scene:) will contain familiar rendering code. Renderer supplies ParticlesRenderPass with the view’s current render pass descriptor before calling the draw method. You then create the render encoder using this descriptor.

size contains the view’s drawable size which the vertex shader will require. Renderer calls resize(view:size:) to update size when the view size changes.

➤ Continue by adding the following after the previous code:

```
// 1
for emitter in scene.particleEffects {
  if emitter.currentParticles <= 0 { continue }
  renderEncoder.setRenderPipelineState(
    emitter.blending ? blendingPSO : renderPSO)
  // 2
  renderEncoder.setVertexBuffer(
    emitter.particleBuffer,
```

<a id="page-439"></a>

```
    offset: 0,
    index: 1)
  renderEncoder.setVertexBytes(
    &emitter.position,
    length: MemoryLayout<float2>.stride,
    index: 2)
  renderEncoder.setFragmentTexture(
    emitter.particleTexture,
    index: 0)
  // 3
  renderEncoder.drawPrimitives(
    type: .point,
    vertexStart: 0,
    vertexCount: 1,
    instanceCount: emitter.currentParticles)
}
renderEncoder.endEncoding()
```

Going through the code:

1. For each emitter in the scene, you set the pipeline state object depending upon whether the emitter’s particles require blending.

2. You send the emitter particle buffer and the emitter’s position to the vertex shader. You also set the texture that all the particles will use.

3. You draw a point primitive for each particle. Each particle is an instance, so you set instanceCount to the number of live particles.

## **The Vertex and Fragment Functions**

All right, it’s time to configure the shader functions.

➤ In the Shaders folder, create a new Metal file named Particles.metal, and add the following code:

```
#import "Common.h"

// 1
kernel void computeParticles(
  device Particle *particles [[buffer(0)]],
  uint id [[thread_position_in_grid]])
{
  // 2
  float xVelocity = particles[id].speed
                      * cos(particles[id].direction);
  float yVelocity = particles[id].speed
                      * sin(particles[id].direction);
  particles[id].position.x += xVelocity;
```

<a id="page-440"></a>

```
  particles[id].position.y += yVelocity;
  // 3
  particles[id].age += 1.0;
  float age = particles[id].age / particles[id].life;
  particles[id].scale =  mix(particles[id].startScale,
                             particles[id].endScale, age);
  // 4
  if (particles[id].age > particles[id].life) {
    particles[id].position = particles[id].startPosition;
    particles[id].age = 0;
    particles[id].scale = particles[id].startScale;
  }
}
```

This code:

1. Takes in the particle buffer as a shader function argument and sets a 1D index to iterate over this buffer.

2. Calculates the velocity for each particle and then updates its position by adding the velocity to it.

3. Updates the particle’s age and scales the particle depending on its age.

4. If the particle’s age has reached its total lifespan, reset the particle to its original properties.

➤ Add a new structure for the vertex and fragment shaders:

```
struct VertexOut {
  float4 position  [[position]];
  float  point_size [[point_size]];
  float4 color;
};
```

You’ll draw the particle texture on to a point, so point\_size here will be the size of each particle.

➤ Add the vertex function to process the particle position and color:

```
// 1
vertex VertexOut vertex_particle(
  constant float2 &size [[buffer(0)]],
  const device Particle *particles [[buffer(1)]],
  constant float2 &emitterPosition [[buffer(2)]],
  uint instance [[instance_id]])
{
  // 2
  float2 position = particles[instance].position
```

<a id="page-441"></a>

```
    + emitterPosition;
  VertexOut out {
    // 3
    .position =
      float4(position.xy / size * 2.0 - 1.0, 0, 1),
    // 4
    .point_size = particles[instance].size
      * particles[instance].scale,
    .color = particles[instance].color
  };
  return out;
}
```

Going through this code:

1. Get the drawable size from the CPU as well as the updated particle buffer and the emitter’s position, and use a 1D index to iterate over all particles.

2. Offset the particle position by the emitter’s position.

3. Map the particle positions from a [0, 1] range to a [-1, 1] range so that the middle of the screen is now the origin (0, 0).

4. Set the particle’s point size and color.

➤ Add the fragment shader:

```
// 1
fragment float4 fragment_particle(
  VertexOut in [[stage_in]],
  texture2d<float> particleTexture [[texture(0)]],
  float2 point [[point_coord]])
{
  // 2
  constexpr sampler default_sampler;
  float4 color = particleTexture.sample(default_sampler, point);
  // 3
  if (color.a < 0.5) {
    discard_fragment();
  }
  // 4
  color = float4(color.xyz, 0.5);
  color *= in.color;
  return color;
}
```

<a id="page-442"></a>

Going through this code:

1. Get the processed particle fragments via [[stage\_in]] and the snowflake texture from the CPU. The [[point\_coord]] attribute is generated by the rasterizer and is a 2D coordinate that indicates where the current fragment is located within a point primitive in a [0, 1] range.

2. Create a sampler, and use it to sample from the given texture at the current fragment position.

3. Apply alpha testing so you don’t render the fragment at low alpha values.

4. Return the texture color combined with the particle color.

## Conﬁguring Particle Effects

The particle computing and rendering structure is complete. All you have to do now is configure an emitter for snow particles.

➤ Open ParticleEffects.swift.

You’ll create a factory method for each particle effect. In it, you’ll set up a particle descriptor and return an Emitter. A fire emitter is already set up in ParticleEffects, giving you a preview of what snow emitter is going to look like.

➤ Add this to ParticleEffects:

```
static func createSnow(size: CGSize) -> Emitter {
  // 1
  var descriptor = ParticleDescriptor()
  descriptor.positionXRange = 0...Float(size.width)
  descriptor.direction = -.pi / 2
  descriptor.speedRange = 2...6
  descriptor.pointSizeRange = 80 * 0.5...80
  descriptor.startScale = 0
  descriptor.startScaleRange = 0.2...1.0
  // 2
  descriptor.life = 500
  descriptor.color = [1, 1, 1, 1]
  // 3
  return Emitter(
    descriptor,
    texture: "snowflake",
    particleCount: 100,
    birthRate: 1,
    birthDelay: 20)
}
```

<a id="page-443"></a>

Here’s what’s happening:

1. The descriptor describes how to initialize each particle. You set up ranges for position, speed and scale. Particles will appear at the top of the screen in random positions.

2. A particle has an age and a life-span. A snowflake particle will remain alive for 500 frames and then recycle. You want the snowflake to travel from the top of the screen all the way down to the bottom of the screen. life has to be long enough for this to happen. If you give your snowflake a short life, it will disappear while still on screen.

3. You tell the emitter how many particles in total should be in the system. birthRate and birthDelay control how fast the particles emit. With these parameters, you’ll emit one snowflake every twenty frames until there are 100 snowflakes in total. If you want a blizzard rather than a few flakes, then you can set the birthrate higher and the delay between each emission less.

Particle parameters are really fun to experiment with. Once you have your snowflakes falling, change any of these parameters to see what the effect is.

➤ Open GameScene.swift, and add this to update(size: CGSize):

```
let snow = ParticleEffects.createSnow(size: size)
snow.position = [0, Float(size.height) + 100]
particleEffects = [snow]
```

You set up the emitter off the top of the screen, so that particles don’t suddenly pop in. You then add it to the scene’s list of particles. Whenever the view resizes, you will reset the particle effects to fit in the new size.

➤ Build and run the app, and enjoy the relaxing snow with variable snowflake speeds and sizes:

![Figure](Metal_by_Tutorials_v500mpdf/83e9e25648158731985c5f4c.png)

_A snow particle system_

<a id="page-444"></a>

Go back and experiment with some of the particle settings. With particleCount of 800, birthDelay of 2 and speedRange of 4...8, you start off with a gentle snowfall that gradually turns into a veritable blizzard.

## **Fire**

Brrr… that snow is so cold. Let’s build a fire to warm you up!

➤ Open **GameScene.swift**, and replace `particleEffects = [snow]` with:

```
let fire = ParticleEffects.createFire(size: size)
fire.position = [0, 0]
particleEffects = [snow, fire]
```

You position the new fire emitter just off the bottom of the screen.

➤ Open ParticleEffects.swift and examine the createFire(size:) settings, and see if you can work out what the particle system will look like.

You’re loading more particles than for snow, and a different texture. The birth rate is higher, and there’s no delay. The direction is upwards, with a slight variation in range. The particle scales down over its life. The color is fiery orange with blending enabled.

➤ Build and run to see this new particle system in action.

![Figure](Metal_by_Tutorials_v500mpdf/f428cb5fc4c83323aeb743d2.png)

_Fire and snow_

<a id="page-445"></a>

## **Key Points**

• Particle emitters emit particles. These particles carry information about themselves, such as position, velocity and color.

• Particle attributes can vary over time. A particle may have a life and decay after a certain amount of time.

• As each particle in a particle system has the same attributes, the GPU is a good fit for updating them in parallel.

• Particle systems, depending on given attributes, can simulate physics or fluid systems, or even hair and grass systems.

## **Where to Go From Here?**

You’ve only just begun playing with particles. There are many more particle characteristics you could include in your particle system:

• Color over life.

• Gravity.

• Acceleration.

• Instead of scaling linearly over time, how about scaling slowly then faster?

The code in Chapter 30, “Profiling”, includes fire particles in three dimensions.

If you want more ideas, review the links in this chapter’s references.markdown.

There are some things you haven’t yet looked at, like collisions or reaction to acting forces. You have also not read anything about intelligent agents and their behaviors. You’ll learn more about all this next, in Chapter 18, “Particle Behavior”.

<a id="page-446"></a>

# 18

# Chapter 18: Particle Behavior

As you learned in the previous chapter, particles have been at the foundation of computer animation for years. In computer graphics literature, three major animation paradigms are well defined and have rapidly evolved in the last two decades:

• Keyframe animation: Starting parameters are defined as initial frames, and then an interpolation procedure is used to fill the remaining values for in-between frames. You’ll cover this topic in Chapter 23, “Animation”.

• Physically based animation: Starting values are defined as animation parameters, such as a particle’s initial position and velocity, but intermediate values are not specified externally. This topic was covered in Chapter 17, “Particle Systems”.

• Behavioral animation: Starting values are defined as animation parameters. In addition, a cognitive process model describes and influences the way intermediate values are later determined.

In this chapter, you’ll focus on the last paradigm as you work through:

• Velocity and bounds checking.

• Swarming behavior.

• Behavioral animation.

• Behavioral rules.

<a id="page-447"></a>

By the end of the chapter, you’ll build and control a swarm exhibiting basic behaviors you might see in nature.

![Figure](Metal_by_Tutorials_v500mpdf/799f982e4a5dffe8e516d027.png)

_Flocking_

## **Behavioral Animation**

You can broadly split behavioral animation into two major categories:

• Cognitive behavior: This is the foundation of artificial life which differs from artificial intelligence in that AI objects do not exhibit behaviors or have their own preferences. It can range from a simple cause-and-effect based system to more complex systems, known as agents, that have a psychological profile influenced by the surrounding environment.

• Aggregate behavior: Think of this as the overall outcome of a group of agents. This behavior is based on the individual rules of each agent and can influence the behavior of neighbors.

In this chapter, you’ll keep your focus on aggregate behavior.

<a id="page-448"></a>

There’s a strict correlation between the various types of aggregate behavior entities and their characteristics. In the following table, notice how the presence of a physics system or intelligence varies between entity types.

![Figure](Metal_by_Tutorials_v500mpdf/28a2267a9d7442ce1714eaf3.png)

• Particles are the largest aggregate entities and are mostly governed by the laws of physics, but they lack intelligence.

• Flocks are an entity that’s well-balanced between size, physics and intelligence.

• Crowds are smaller entities that are rarely driven by physics rules and are highly intelligent.

Working with crowd animation is a challenging and rewarding experience. However, the purpose of this chapter is to describe and implement a flocking-like system, or to be more precise, a swarm of insects.

## **Swarming Behavior**

Swarms are gatherings of insects or other small-sized beings. The swarming behavior of insects can be modeled in a similar fashion as the flocking behavior of birds, the herding behavior of animals or the shoaling behavior of fish.

You know from the previous chapter that particle systems are fuzzy objects whose dynamics are mostly governed by the laws of physics. There are no interactions between particles, and usually, they are unaware of their neighboring particles. In contrast, swarming behavior uses the concept of neighboring quite heavily.

<a id="page-449"></a>

The swarming behavior follows a set of basic movement rules developed in 1986 by Craig Reynolds in an artificial flocking simulation program known as Boids. Since this chapter is heavily based on his work, the term boid will be used throughout the chapter instead of particle.

Initially, this basic set only included three rules: cohesion, separation and alignment. Later, more rules were added to extend the set to include a new type of agent; one that has autonomous behavior and is characterized by the fact that it has more intelligence than the rest of the swarm. This led to defining new models such as follow-the-leader and predator-prey.

Time to transform all of this knowledge into a swarm of quality code.

## **The Starter Project**

➤ In Xcode, open, build and run the starter project for this chapter. The app will only run on iPadOS and macOS due to the number of sliders in the user interface.

![Figure](Metal_by_Tutorials_v500mpdf/552c0b560704e20952899e7e.png)

_The starter app_

The app has a number of exciting sliders that mostly don’t do anything just yet, but you’ll make them work throughout this chapter. You can change ParticleCount from 2 to 1,000 particles.

<a id="page-450"></a>

In Xcode, these are the files of interest:

• Common.h defines the Particle structure, also aliased as Boid. Params matches the slider values, which the kernel shader function will use.

• Emitter.swift creates a buffer containing the particles. Each particle has a position attribute and a velocity attribute. The initializer sets these to random values. Particle zero will be a predator boid, so is treated differently from the other boids.

• Renderer initializes the emitter at the beginning of the app and whenever the particle count changes. draw(in:) first clears the texture using the clearScreen compute shader from the previous project. draw(in:) then dispatches threads for the number of particles to calculate the boids’ positions. The dispatch code contains an example of both macOS code and iOS code where non-uniform threads are not supported.

• Flocking.metal contains two kernel functions. One clears the drawable texture, and the other writes a pixel, representing a boid, to the given texture. You’ll calculate boid zero individually, so it’s colored red.

• Helper.metal contains two functions that will keep the boids on-screen.

There’s a problem in the app: a visibility issue. In its current state, the boids are barely distinguishable despite being white on a black background.

There’s a neat trick you can apply in cases like this when you don’t want to use a texture for boids (like you used in the previous chapter). In fact, scientific simulations and computational fluid dynamics projects very rarely use textures, if ever.

You can’t use the [[point\_size]] attribute here because you’re not rendering in the traditional sense. Instead, you’re writing pixels in a kernel function directly to the drawable’s texture.

<a id="page-451"></a>

The trick is to “paint” the surrounding neighbors of each boid, which makes the current boid seem larger than it really is.

![Figure](Metal_by_Tutorials_v500mpdf/32a53ac144f710235841078f.png)

_Painting the pixels around the boid_

➤ In Flocking.metal, at the end of the flocking kernel function, replace output.write(color, location); with:

```
int size = 4;
for (int x = -size; x <= size; x++) {
  for (int y = -size; y <= size; y++) {
    output.write(color, location + uint2(x, y));
  }
}
```

This code modifies two neighboring pixels around all sides of the boid which causes the boid to appear larger.

➤ Build and run the app, and you’ll see that the boids are more distinguishable now.

![Figure](Metal_by_Tutorials_v500mpdf/f2a3915e959d313b207b03a2.png)

_Larger boids_

That’s a good start, but how do you get them to move around? For that, you need to look into velocity.

<a id="page-452"></a>

## **Velocity**

Velocity is a vector made up of two other vectors: direction and speed. The speed is the magnitude or length of the vector, and the direction is given by the linear equation of the line on which the vector lies.

![Figure](Metal_by_Tutorials_v500mpdf/8455e985d5846c0e90d6b195.png)

_Properties of a vector_

➤ Open **Common.h**, and check out the `Particle` structure:

```
struct Particle {
  vector_float2 position;
  vector_float2 velocity;
};

typedef struct Particle Boid;
```

These two properties are all you need to make your flock swarm. You can use the term Boid in place of Particle in your shaders.

➤ Open Flocking.metal, and in flocking, replace // flocking code here with this:

```
float2 velocity = boid.velocity;
position += velocity;
boid.position = position;
boid.velocity = velocity;
boids[id] = boid;
```

This code gets the current velocity, updates the current position with the velocity, and then updates the boid data before storing the new values.

Build and run the app, and you’ll see that the boids are now moving everywhere on the screen and… uh, wait! It looks like they’re disappearing from the screen too. What happened?

<a id="page-453"></a>

Although you set the velocity to random values, you still need a way to force the boids to stay on the screen. Essentially, you need a way to make the boids bounce back when they hit any of the edges.

![Figure](Metal_by_Tutorials_v500mpdf/7ead0afbd8f36af910e81c0a.png)

_Reflect and bounce at the edges_

For this function to work, you need to add checks for X and Y to make sure the boids stay in the rectangle defined by the origin and the size of the window, in other words, the width and height of your scene.

➤ Open Helper.metal and examine bounceBoid. If the boid position gets outside the screen, you change the velocity sign, which changes the direction of the moving boid.

➤ In **Flocking.metal**, in `flocking`, replace:

```
boid.position = position;
boid.velocity = velocity;
```

With:

```
float2 viewSize = float2(output.get_width(),
output.get_height());
boid = bounceBoid(position, velocity, viewSize);
```

You check that the boid is still on-screen. If not, bounce the boid at the edge.

<a id="page-454"></a>

➤ Build and run the app, and you’ll see that the boids are now bouncing back when hitting an edge.

![Figure](Metal_by_Tutorials_v500mpdf/9eef10f8913ba2c0bdf74032.png)

_Bouncing boids_

Currently, the boids only obey the laws of physics. They’ll travel to random locations with random velocities, and they’ll stay on the window screen because of a few strict physical rules you’re imposing on them.

The next stage is to make the boids behave as if they are able to think for themselves.

## **Behavioral Rules**

There’s a basic set of steering rules that swarms and flocks can adhere to, and it includes:

• Cohesion

• Separation

• Alignment

• Escaping

You’ll learn about each of these rules as you implement them in your project.

<a id="page-455"></a>

## **Cohesion**

Cohesion is a steering behavior that causes the boids to stay together as a group. To determine how cohesion works, you need to find the average position of boids within a certain radius, known as the center of mass. Each neighboring boid will then apply a steering force in the direction of this center and converge near the center.

![Figure](Metal_by_Tutorials_v500mpdf/858cdb73168848e5fd0f7362.png)

_Cohesion_

App sliders provide values for:

• Cohesion Strength: A toning down factor that lets you relax the cohesion rule.

• Radius for neighbors: Any boid within this radius is included in the current boid’s steering calculation.

➤ In Flocking.metal, create a new function for cohesion before the flocking function:

```
float2 cohesion(Params params, uint index, device Boid* boids) {
  // 1
  Boid thisBoid = boids[index];
  float neighborsCount = 0;
  float2 cohesion = 0.0;
  // 2
  for (uint i = 1; i < params.particleCount; i++) {
    Boid boid = boids[i];
    float d = distance(thisBoid.position, boid.position);
    if (d < params.neighborRadius && i != index) {
      cohesion += boid.position;
      neighborsCount++;
    }
  }
```

<a id="page-456"></a>

```
  // 3
  if (neighborsCount > 0) {
    cohesion /= neighborsCount;
    cohesion -= thisBoid.position;
    cohesion *= params.cohesionStrength;
  }
  return cohesion;
}
```

Going through the code:

1. Isolate the current boid at the given index from the rest of the group. Define the cohesion value and number of neighbors.

2. Loop through all of the boids in the swarm, and accumulate each boid’s position to the cohesion variable. You start from index 1, as boid[0] will be a special case.

3. Get an average position value for the neighborhood, and subtract the current boid’s position to calculate the target position. Take into account the cohesion strength slider.

➤ In flocking, add this code immediately before position += velocity:

```
float2 cohesionVector = cohesion(params, id, boids);

// velocity accumulation
velocity += cohesionVector;
```

Here, you accumulate the boid’s velocity with the steering forces. You’ll build upon the velocity accumulation as you go ahead with new behavioral rules.

➤ Build and run the app, and set Cohesion Strength to 0.01. Notice how the boids are initially trying to get away — following their random directions. Moments later, they’re pulled back toward the center of the flock.

![Figure](Metal_by_Tutorials_v500mpdf/8a4d61561e990384b801074d.png)

_Converging boids_

<a id="page-457"></a>

As the simulation runs, the speed of the boids gets out of control.

➤ Add a new function before cohesion:

```
float2 checkSpeed(float2 vector, float minSpeed, float maxSpeed)
{
  float speed = length(vector);
  if (speed < minSpeed) {
    return vector / speed * minSpeed;
  }
  if (speed > maxSpeed) {
    return vector / speed * maxSpeed;
  }
  return vector;
}
```

Recall from the beginning of the chapter, that the length of a vector gives you the speed. You then check that the vector is within minimum and maximum speed constraints.

➤ In flocking, call this new function before position += velocity;:

```
velocity =
  checkSpeed(velocity, params.minSpeed, params.maxSpeed);
```

You use the minimum and maximum speed slider values to control the boids’ speed.

➤ Build and run the app, and experiment with the new active sliders.

![Figure](Metal_by_Tutorials_v500mpdf/4039381ca80c7d68deb6f019.png)

_Cohesion with a strength of 0.01_

<a id="page-458"></a>

## **Separation**

Separation is another steering behavior that allows a boid to stay a certain distance from nearby neighbors. This is accomplished by applying a repulsion force to the current boid when the set threshold for proximity is reached.

![Figure](Metal_by_Tutorials_v500mpdf/3747c423b47cc1fddca32e72.png)

_Separation_

In addition to the neighbor radius, app sliders provide values for:

• Separation Strength: The strength of the force.

• Separation Radius: The distance between each boid.

➤ Add the new separation function before flocking:

```
float2 separation(Params params, uint index, device Boid* boids)
{
  // 1
  Boid thisBoid = boids[index];
  float2 separation = float2(0);
  // 2
  for (uint i = 1; i < params.particleCount; i++) {
    Boid boid = boids[i];
    if (i != index) {
      if (abs(distance(boid.position, thisBoid.position))
            < params.separationRadius) {
        separation -= (boid.position - thisBoid.position);
      }
    }
  }
  // 3
  separation *= params.separationStrength;
  return separation;
}
```

<a id="page-459"></a>

Going through the code:

1. Isolate the current boid at the given index from the rest of the group. Define and initialize position.

2. Loop through all of the boids in the swarm (except boid[0]). If this is a boid other than the isolated one, check the distance between the current and isolated boids. If the distance is smaller than the proximity threshold, update the position to keep the isolated boid within a safe distance.

3. Attenuate the separation force by the strength slider’s value.

➤ In `flocking`, before the `// velocity accumulation` comment, add this:

`float2 separationVector = separation(params, id, boids);`

➤ Then, update velocity to include the separation contribution:

`velocity += cohesionVector + separationVector;`

➤ Build and run the project. Change the ParticleCount and Separation radius sliders to see the counter-effect of pushing back from cohesion as a result of the separation contribution.

![Figure](Metal_by_Tutorials_v500mpdf/a236888e517b50a2707a535e.png)

_Boid separation_

<a id="page-460"></a>

## **Alignment**

Alignment is the last of the three steering behaviors Reynolds used for his flocking simulation. The main idea is to calculate an average of the velocities for a limited number of neighbors. The resulting average is often referred to as the desired velocity.

With alignment, a steering force gets applied to the current boid’s velocity to make it align with the group.

![Figure](Metal_by_Tutorials_v500mpdf/e09df97807cb71412bd71fe4.png)

_Alignment_

The app slider Alignment Strength lets you control the how much the boids conform to the alignment rule.

➤ Add the new alignment function before flocking:

```
float2 alignment(Params params, uint index, device Boid* boids)
{
  // 1
  Boid thisBoid = boids[index];
  float neighborsCount = 0;
  float2 velocity = 0.0;
  // 2
  for (uint i = 1; i < params.particleCount; i++) {
    Boid boid = boids[i];
    float d = distance(thisBoid.position, boid.position);
    if (d < params.neighborRadius && i != index) {
      velocity += boid.velocity;
      neighborsCount++;
    }
  }
  // 3
  if (neighborsCount > 0) {
    velocity = velocity / neighborsCount;
```

<a id="page-461"></a>

```
    velocity = (velocity - thisBoid.velocity);
    velocity *= params.alignmentStrength;
  }
  return velocity;
}
```

Going through the code:

1. As you did before, isolate the current boid at the given index from the rest of the group. Define and initialize velocity. Because this force only includes neighbors, define and initialize the number of boids in the neighborhood.

2. Loop through all of the boids in the swarm (except boid[0]), and accumulate each boid’s velocity to the velocity variable.

3. Get an average velocity value for the neighborhood and attenuate by the slider strength.

➤ In `flocking`, before the `// velocity accumulation` comment, add this code:

`float2 alignmentVector = alignment(params, id, boids);`

➤ Then, update the velocity accumulation code so that it includes the alignment contribution:

`velocity += cohesionVector + separationVector + alignmentVector;`

To get the full effect of this alignment, instead of bouncing the boids at the edge of the view, you’ll wrap them so that when the boid goes off the left of the view, it’ll reappear at the right of the view. Similarly, when it disappears off the top, it’ll reappear at the bottom of the view.

➤ Replace `boid = bounceBoid(position, velocity, viewSize);` with:

```
if (id == 0) {
  boid = bounceBoid(position, velocity, viewSize);
} else {
  boid.position = wrapPosition(position, viewSize);
  boid.velocity = velocity;
}
```

You use the helper function in Helper.metal to wrap the boids around the view. boid[0] will be the only boid that bounces.

<a id="page-462"></a>

➤ Build and run the app, slide the Cohesion and Separation Strength sliders to zero, and Alignment Strength to 0.10. As boids meet each other, they will adjust until the whole flock is going in the same direction. If you want to reset the simulation, use the ParticleCount slider to change the number of particles.

![Figure](Metal_by_Tutorials_v500mpdf/0acfa4e0ae2d8a7ef59dc1b8.png)

_Boids aligning_

## **Escaping**

Escaping is a new type of steering behavior that introduces an agent with autonomous behavior and slightly more intelligence — the predator (also known as boid[0]).

In the predator-prey behavior, the predator tries to approach the closest prey, while the neighboring boids try to escape.

![Figure](Metal_by_Tutorials_v500mpdf/a58af4d3e7216960f29c1de8.png)

_Escaping_

<a id="page-463"></a>

First, set up the predator’s movement.

➤ Create a new function before flocking:

```
float2 updatePredator(Params params, device Boid* boids)
{
  float2 preyPosition = boids[0].position;
  for (uint i = 1; i < params.particleCount; i++) {
    float d = distance(preyPosition, boids[i].position);
    if (d < params.predatorSeek) {
      preyPosition = boids[i].position;
      break;
    }
  }
  return preyPosition - boids[0].position;
}
```

Just like before, you use the slider values to loop through the boids and find the first boid within the seek radius around the predator’s current position.

Note: If you want to find the closest boid, you should loop through all of them, and not break out of the for loop.

➤ In `flocking`, right after `float2 velocity = boid.velocity;`, add this:

```
if (id == 0) {
  float2 predatorVector = updatePredator(params, boids);
  velocity += predatorVector;
  velocity =
    checkSpeed(velocity, params.minSpeed, params.predatorSpeed);
} else {
```

You update the predator’s position, if the thread id is 0. All the velocity accumulation will go in the else part of the conditional that updates the rest of the boids. The predator has a different maximum speed from the other boids so you can control its eagerness for prey.

➤ Terminate the conditional before position += velocity;:

`}`

➤ Add the new escaping function before flocking:

```
float2 escaping(Params params, Boid predator, Boid boid) {
  float2 velocity = boid.velocity;
  float d = distance(predator.position, boid.position);
```

<a id="page-464"></a>

```
  if (d < params.predatorRadius) {
    velocity = boid.position - predator.position;
    velocity *= params.predatorStrength;
  }
  return velocity;
}
```

If a boid is within a certain radius of the predator, the boid reverses velocity.

➤ In `flocking`, before the `// velocity accumulation` comment, add this:

`float2 escapingVector = escaping(params, boids[0], boid);`

➤ Then, update the velocity accumulation code to include the escaping contribution:

```
velocity += cohesionVector + separationVector
 + alignmentVector + escapingVector;
```

➤ Build and run the app. Notice that some of the boids are steering away from the group and avoiding the red predator.

![Figure](Metal_by_Tutorials_v500mpdf/448ef74afc9a94c702b3e1ee.png)

_Escaping boids_

If the predator is lucky enough to catch a prey, it will stay with the prey until they reach an edge. The prey will then escape by wrapping around, while the predator will bounce.

Experiment with the sliders and see what effects you can make. Instead of considering boid[0] as a “predator”, you can consider it a random force to manipulate the direction of swarms of boids.

<a id="page-465"></a>

## **Key Points**

• You can give particles behavioral animation by causing them to react with other particles

• Swarming behavior has been widely researched. The Boids simulation describes basic movement rules.

• The behavioral rules for boids include cohesion, separation and alignment.

• Adding a predator to the particle mass requires an escaping algorithm.

## **Where to Go From Here?**

In this chapter, you learned how to construct basic behaviors and apply them to a small flock. Continue developing your project by adding a colorful background and textures for the boids. Or make it a 3D flocking app by adding projection to the scene. When you’re done, add the flock animation to your engine. Whatever you do, the sky is the limit.

This chapter barely scratched the surface of what is widely known as behavioral animation. Be sure to review the references.markdown file in the chapter directory for links to more resources about this wonderful topic.

<a id="page-466"></a>

# **Section III: Advanced Metal**

In this section, you’ll learn many advanced features of Metal and explore realistic rendering techniques. You’ll animate characters, and also manage your resources more effectively.

<a id="page-467"></a>

# 19

# Chapter 19: Tessellation &amp; Terrains

So far, you’ve used normal map trickery in the fragment function to show the fine details of your low poly models. To achieve a similar level of detail without using normal maps requires a change of model geometry by adding more vertices. The problem with adding more vertices is that when you send them to the GPU, it chokes up the pipeline. Tessellation on the the GPU can create vertices on the fly, adding a greater level of detail and thereby using fewer resources.

In this chapter, you’ll create a detailed terrain using a small number of points. You’ll send a flat ground plane with a grayscale texture describing the height, and the tessellator will create as many vertices as needed. The vertex function will then read the texture and displace (move) these new vertices vertically.

![Figure](Metal_by_Tutorials_v500mpdf/ef4133608e8b050dbfe51184.png)

_Tessellation concept_

In this example, on the left side are the control points. On the right side, the tessellator creates extra vertices, with the number dependent on how close the control points are to the camera.

<a id="page-468"></a>

## **Tessellation**

For tessellation, instead of sending vertices to the GPU, you send patches. These patches are made up of control points — a minimum of three for a triangle patch, or four for a quad patch. The tessellator can convert each quad patch into a certain number of triangles: up to 4,096 triangles on a recent iMac and 256 triangles on an iPhone that’s capable of tessellation.

Note: Tessellation is not available in Simulator.

With tessellation, you can:

• Send less data to the GPU. Because the GPU doesn’t store tessellated vertices in graphics memory, it’s more efficient on resources.

• Make low poly objects look less low poly by curving patches.

• Displace vertices for fine detail instead of using normal maps to fake it.

• Decide on the level of detail based on the distance from the camera. The closer an object is to the camera, the more vertices it contains.

## **The Starter Project**

➤ Open the starter project for this chapter.

So that you can more easily understand the difference between rendering patches and rendering vertices, the starter project is a simplified renderer.

All the rendering code is in Renderer.swift, with the pipeline state setup in Pipelines.swift. Quad.swift contains the vertices and vertex buffer for the quad, and a method to generate control points.

This code is the minimum needed for a simple render of six vertices to create a quad.

<a id="page-469"></a>

➤ Build and run the project.

![Figure](Metal_by_Tutorials_v500mpdf/cd004dae5e6e18ae11e02ccb.png)

_The starter app_

Your task in this chapter is to convert this quad to a terrain made up of patch quads with many vertices.

Before creating a tessellated terrain, you’ll tessellate a single four-point patch. Instead of sending six vertices to the GPU, you’ll send the positions of the four corners of the patch. You’ll give the GPU edge factors and inside factors which tell the tessellator how many vertices to create. You’ll render in wireframe line mode so you can see the vertices added by the tessellator, but you can change this with the Wireframe toggle in the app.

To convert the quad, you’ll do the following on the CPU side:

![Figure](Metal_by_Tutorials_v500mpdf/2c892c0dede061a27bd518fb.png)

_CPU pipeline_

On the GPU side, you’ll set up a tessellation kernel that processes the edge and inside factors. You’ll also set up a post-tessellation vertex shader that handles the vertices generated by the hardware tessellator.

![Figure](Metal_by_Tutorials_v500mpdf/e5d8c4e2f30b7bae4cf20842.png)

_GPU pipeline_

<a id="page-470"></a>

## **Tessellation Patches**

A patch consists of a certain number of control points, generally:

• bilinear: Four control points, one at each corner

• biquadratic: Nine control points

• bicubic: Sixteen control points

![Figure](Metal_by_Tutorials_v500mpdf/4681427a1d1c882f802b4356.png)

_Tessellated patches_

The control points make up a cage which is made up of spline curves. A spline is a parametric curve made up of control points. There are various algorithms to interpolate these control points. But here, A, B and C are the control points. As point P travels from A to B, point Q travels from B to C. The half way point between P and Q describes the blue curve.

![Figure](Metal_by_Tutorials_v500mpdf/7ee582eafb35044864c53234.png)

_A bezier curve_

To create the curved patch surface, the vertex function interpolates vertices to follow this parametric curve.

Note: Because the mathematics of curved surfaces is quite involved, you’ll work with only four control points per patch in this chapter.

<a id="page-471"></a>

## **Tessellation Factors**

For each patch, you need to specify inside edge factors and outside edge factors. The four-point patch in the following image shows different edge factors for each edge — specified as [2, 4, 8, 16] — and two different inside factors — specified as [8, 16], for horizontal and vertical respectively.

![Figure](Metal_by_Tutorials_v500mpdf/ee851c3fa491f5429c4d8c1c.png)

_Edge factors_

The edge factors specify how many segments an edge will be split into. An edge factor of 2 has two segments along the edge. For the inside factors, look at the horizontal and vertical center lines. In this example, the horizontal center has eight segments, and the vertical center has sixteen.

Although only four control points (shown in red) went to the GPU, the hardware tessellator created a lot more vertices. However, creating more vertices on a flat plane doesn’t make the render any more interesting. Later, you’ll find out how to move these vertices around in the vertex function to make a bumpy terrain. But first, you’ll discover how to tessellate a single patch.

➤ In **Renderer.swift**, in `Renderer`, add the following properties:

```
let patches = (horizontal: 1, vertical: 1)
var patchCount: Int {
  patches.horizontal * patches.vertical
}
```

You create a constant for the number of patches you’re going to create, in this case, one. patchCount is a convenience property that returns the total number of patches.

➤ Next, add this:

```
var edgeFactors: [Float] = [4]
var insideFactors: [Float] = [4]
```

<a id="page-472"></a>

Here, you set up the edge and inside factors as Float array properties. These variables indicate four segments along each edge, and four in the middle.

You can specify different factors for different edges by adding them to the array. For each patch, the GPU processes these edge factors and places the amount to tessellate each into a buffer.

➤ Create a property to provide a buffer of the correct length:

```
lazy var tessellationFactorsBuffer: MTLBuffer? = {
  // 1
  let count = patchCount * (4 + 2)
  // 2
  let size = count * MemoryLayout<Float>.size / 2
  return Renderer.device.makeBuffer(
    length: size,
    options: .storageModePrivate)
}()
```

1. count is the number of patches multiplied by the four edge factors and two inside factors.

2. Here you calculate the size of the buffer. In the tessellation kernel, you’ll fill the buffer with a special type consisting of half-floats.

Now it’s time to set up the patch data.

## **Setting Up the Patch Data**

Instead of an array of six vertices, you’ll create a four-point patch with control points at the corners. Currently, in Quad.swift, Quad holds a vertexBuffer property that contains the vertices. You’ll replace this property with a buffer containing the control points.

➤ In `Renderer`, add the following property:

`var controlPointsBuffer: MTLBuffer?`

➤ At the end of `init(metalView:options:)`, fill the buffer with control points:

```
let controlPoints = Quad.createControlPoints(
  patches: patches,
  size: (2, 2))
controlPointsBuffer =
  Renderer.device.makeBuffer(
    bytes: controlPoints,
    length: MemoryLayout<float3>.stride * controlPoints.count)
```

<a id="page-473"></a>

Quad.swift contains a method, createControlPoints(patches:size:). This method takes in the number of patches, and the unit size of the total number of patches. It then returns an array of xyz control points. Here, you create a patch with one corner at [-1, 0, 1], and the diagonal at [1, 0, -1]. This is a flat horizontal plane, but Renderer’s modelMatrix rotates the patch by 90º so you can see the patch vertices.

## **Set Up the Render Pipeline State**

You can configure the tessellator by changing the pipeline state properties. Until now, you’ve processed only vertices with the vertex descriptor. However, you’ll now modify the vertex descriptor so it processes patches instead.

➤ Open Pipelines.swift, and in createRenderPSO(), where you set up vertexDescriptor, add this:

`vertexDescriptor.layouts[0].stepFunction = .perPatchControlPoint`

With the old setup, you were using a default stepFunction of .perVertex. With that setup, the vertex function fetches new attribute data every time a new vertex is processed.

Now that you’ve moved on to processing patches, you need to fetch new attribute data for every control point.

## **The Tessellation Kernel**

To calculate the number of edge and inside factors, you’ll set up a compute pipeline state object that points to the tessellation kernel shader function.

➤ Open Renderer.swift, and add a new property to Renderer:

`var tessellationPipelineState: MTLComputePipelineState`

➤ In `init(metalView:options:)`, before `super.init()`, add this:

```
tessellationPipelineState =
  PipelineStates.createComputePSO(function: "tessellation_main")
```

Here, you instantiate the pipeline state for the compute pipeline.

<a id="page-474"></a>

## **Compute Pass**

You now have a compute pipeline state and an MTLBuffer containing the patch data. You also created an empty buffer which the tessellation kernel will fill with the edge and inside factors. Next, you need to create the compute command encoder to dispatch the tessellation kernel.

➤ In `tessellation(commandBuffer:)`, add the following:

```
guard let computeEncoder =
  commandBuffer.makeComputeCommandEncoder() else { return }
computeEncoder.setComputePipelineState(
  tessellationPipelineState)
computeEncoder.setBytes(
  &edgeFactors,
  length: MemoryLayout<Float>.size * edgeFactors.count,
  index: 0)
computeEncoder.setBytes(
  &insideFactors,
  length: MemoryLayout<Float>.size * insideFactors.count,
  index: 1)
computeEncoder.setBuffer(
  tessellationFactorsBuffer,
  offset: 0,
  index: 2)
```

draw(in:) calls tessellation(commandBuffer:) before any rendering. You create a compute command encoder and bind the edge and inside factors to the compute function (the tessellation kernel). If you have multiple patches, the compute function will operate in parallel on each patch, on different threads.

➤ To tell the GPU how many threads you need, continue by adding this after the previous code:

```
let width = min(
  patchCount,
  tessellationPipelineState.threadExecutionWidth)
let gridSize =
  MTLSize(width: patchCount, height: 1, depth: 1)
let threadsPerThreadgroup =
  MTLSize(width: width, height: 1, depth: 1)
computeEncoder.dispatchThreadgroups(
  gridSize,
  threadsPerThreadgroup: threadsPerThreadgroup)
computeEncoder.endEncoding()
```

<a id="page-475"></a>

The compute grid is one dimensional, with a thread for each patch. Before changing the render encoder so it’ll draw patches instead of vertices, you’ll need to create the tessellation kernel.

## **The Tessellation Kernel Function**

➤ In the Shaders folder, create a new Metal file named Tessellation.metal, and add this:

```
#import "Common.h"

kernel void
  tessellation_main(
    constant float *edge_factors [[buffer(0)]],
    constant float *inside_factors [[buffer(1)]],
    device MTLQuadTessellationFactorsHalf
      *factors [[buffer(2)]],
    uint pid [[thread_position_in_grid]])
{
}
```

kernel specifies the type of shader. The function operates on all threads (i.e., all patches) and receives the three things you sent over: the edge factors, inside factors and the empty tessellation factors buffer that you’re going to fill in this function.

The fourth parameter is the patch ID with its thread position in the grid. The tessellation factors buffer consists of an array of edge and inside factors for each patch, and pid gives you the patch index into this array.

➤ Inside the kernel function, add the following:

```
factors[pid].edgeTessellationFactor[0] = edge_factors[0];
factors[pid].edgeTessellationFactor[1] = edge_factors[0];
factors[pid].edgeTessellationFactor[2] = edge_factors[0];
factors[pid].edgeTessellationFactor[3] = edge_factors[0];

factors[pid].insideTessellationFactor[0] = inside_factors[0];
factors[pid].insideTessellationFactor[1] = inside_factors[0];
```

This code fills in the tessellation factors buffer with the edge factors that you sent over. The edge and inside factors array you sent over only had one value each, so you put this value into all factors.

<a id="page-476"></a>

Filling out a buffer with values is a trivial thing for a kernel to do, and you could do this on the CPU. However, as you get more patches and more complexity on how to tessellate these patches, you’ll understand why sending the data to the GPU for parallel processing is a useful step.

After the compute pass is done, the render pass takes over.

## **The Render Pass**

Before doing the render, you need to tell the render encoder about the tessellation factors buffer that you updated during the compute pass.

➤ Open Renderer.swift, and in render(commandBuffer:view:), locate the // draw comment. Just after that comment, add this:

```
renderEncoder.setTessellationFactorBuffer(
  tessellationFactorsBuffer,
  offset: 0,
  instanceStride: 0)
```

The post-tessellation vertex function reads from this buffer that you set up during the kernel function.

Instead of drawing triangles from the vertex buffer, you’ll draw the patch using patch control points from the control points buffer.

➤ Replace:

```
renderEncoder.setVertexBuffer(
  quad.vertexBuffer,
  offset: 0,
  index: 0)
```

With:

```
renderEncoder.setVertexBuffer(
  controlPointsBuffer,
  offset: 0,
  index: 0)
```

➤ Replace the `drawPrimitives` command with this:

```
renderEncoder.drawPatches(
  numberOfPatchControlPoints: 4,
  patchStart: 0,
  patchCount: patchCount,
  patchIndexBuffer: nil,
```

<a id="page-477"></a>

patchIndexBufferOffset: 0,   instanceCount: 1,   baseInstance: 0)

The render command encoder tells the GPU that it’s going to draw one patch with four control points.

## **The Post-Tessellation Vertex Function**

➤ Open Shaders.metal.

The GPU calls the vertex function after the tessellator has done its job of creating the vertices. The function will operate on each one of these new vertices. In the vertex function, you’ll tell each vertex what its position in the rendered quad should be.

➤ Rename VertexIn to ControlPoint.

The definition of position remains the same. Because you used a vertex descriptor to describe the incoming control point data, you can use the [[stage\_in]] attribute.

The vertex function will check the vertex descriptor from the current pipeline state, find that the data is in buffer 0 and use the vertex descriptor layout to read in the data.

➤ Replace `vertex_main` with:

```
// 1
[[patch(quad, 4)]]
// 2
vertex VertexOut
  vertex_main(
// 3
    patch_control_point<ControlPoint> control_points
[[stage_in]],
// 4
    constant Uniforms &uniforms [[buffer(BufferIndexUniforms)]],
// 5
    float2 patch_coord [[position_in_patch]])
{
}
```

<a id="page-478"></a>

This is the post-tessellation vertex function where you return the correct position of the vertex for the rasterizer. Going through the code:

1. The function qualifier tells the vertex function that the vertices are coming from tessellated patches. It describes the type of patch, triangle or quad, and the number of control points, in this case, four.

2. The function is still a vertex shader function as before.

3. patch\_control\_point is part of the Metal Standard Library and provides the per-patch control point data.

4. Uniforms contains the model-view-projection matrix you passed in.

5. The tessellator provides a uv coordinate between 0 and 1 for the tessellated patch so that the vertex function can calculate its correct rendered position.

To visualize how this works, you can temporarily return the UV coordinates as the position and color.

➤ Add the following code to vertex\_main:

```
float u = patch_coord.x;
float v = patch_coord.y;

VertexOut out;
out.position = float4(u, v, 0, 1);
out.color = float4(u, v, 0, 1);
return out;
```

Here, you give the vertex a position as interpolated by the tessellator from the four patch positions, and a color of the same value for visualization.

➤ Build and run the app.

<a id="page-479"></a>

See how the patch is tessellated with vertices between 0 and 1? (Normalized Device Coordinates (NDC) are between -1 and 1 which is why all the coordinates are at the top right.)

![Figure](Metal_by_Tutorials_v500mpdf/3e15ac457ccf2137f6359b55.png)

_Basic tessellation_

To have your vertex positions depend on the patch’s actual position rather than between 0 and 1, you need to interpolate the patch’s control points depending on the UV values.

➤ In `vertex_main`, after assigning the `u` and `v` values, add this:

```
float2 top = mix(
  control_points[0].position.xz,
  control_points[1].position.xz,
  u);
float2 bottom = mix(
  control_points[3].position.xz,
  control_points[2].position.xz,
  u);
```

You interpolate values horizontally along the top of the patch and the bottom of the patch. Notice the index ordering: the patch indices are 0 to 3 clockwise.

![Figure](Metal_by_Tutorials_v500mpdf/e4dd978626660edf278fcc90.png)

_Control point winding order_

<a id="page-480"></a>

You can change this by setting the pipeline descriptor property tessellationOutputWindingOrder to .counterClockwise.

➤ Change the following code:

`out.position = float4(u, v, 0, 1);`

➤ To:

```
float2 interpolated = mix(top, bottom, v);
float4 position = float4(
  interpolated.x, 0.0,
  interpolated.y, 1.0);
out.position = uniforms.mvp * position;
```

You interpolate the vertical value between the top and bottom values and multiply it by the model-view-projection matrix to position the vertex in the scene. Currently, you’re leaving y at 0.0 to keep the patch two-dimensional.

➤ Build and run the app to see your tessellated patch:

![Figure](Metal_by_Tutorials_v500mpdf/d51863d5995fa5620a610da2.png)

_A tessellated patch_

Note: Experiment with changing the edge and inside factors until you’re comfortable with how the tessellator subdivides. For example, change the edge factors array to [2, 4, 8, 16], and change the kernel function so that the appropriate array value goes into each edge.

<a id="page-481"></a>

## **Multiple Patches**

Now that you know how to tessellate one patch, you can tile the patches and choose edge factors that depend on dynamic factors, such as distance.

➤ Open **Renderer.swift**, and change the `patches` initialization to:

`let patches = (horizontal: 2, vertical: 2)`

➤ Build and run the app to see the four patches joined together:

![Figure](Metal_by_Tutorials_v500mpdf/c7e6a45aa6e22b042235ef04.png)

_Four tessellated patches_

In the vertex function, you can identify which patch you’re currently processing using the [[patch\_id]] attribute.

➤ Open Shaders.metal, and add this parameter to vertex\_main:

`uint patchID [[patch_id]]`

➤ Change the assignment of `out.color` to:

```
out.color = float4(0);
if (patchID == 0) {
  out.color = float4(1, 0, 0, 1);
}
```

<a id="page-482"></a>

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/ab5719b1eca646d833ccab93.png)

_Colored by patch id_

Notice how the GPU colors the bottom left patch red. This is the first patch in the control points array.

## **Tessellation By Distance**

Next, you’re going to create a terrain with patches that are tessellated according to the distance from the camera. When you’re close to a mountain, you need to see more detail; when you’re farther away, less. Having the ability to dial in the level of detail is where tessellation comes into its own. By setting the level of detail, you save on how many vertices the GPU has to process in any given situation.

➤ Open **Common.h**, and add the following code:

```
typedef struct {
  vector_float2 size;
  float height;
  uint32_t maxTessellation;
} Terrain;
```

You set up a new structure to describe the size and maximum tessellation of the terrain. You’ll use height for scaling vertices on the y-axis later.

<a id="page-483"></a>

➤ Open Renderer.swift, and add a new constant to Renderer:

`static let maxTessellation = 16`

This value is the maximum amount you will tessellate per patch. On modern Apple Silicon, the maximum amount allowed by the hardware is 64. You can check the maximum in Apple’s Metal Feature Set Tables document (https://is.gd/52uVY9).

➤ Add a new property:

```
var terrain = Terrain(
  size: [2, 2],
  height: 1,
  maxTessellation: UInt32(Renderer.maxTessellation))
```

You describe the terrain with four patches and a maximum height of one unit.

➤ Locate where you set up controlPoints in init(metalView:options:), and change it to:

```
let controlPoints = Quad.createControlPoints(
  patches: patches,
  size: (width: terrain.size.x, height: terrain.size.y))
```

Because your terrains are going to be much larger, you’ll use the terrain constant to create the control points.

To calculate edge factors that are dependent on the distance from the camera, you will send the camera position, model matrix and control points to the kernel.

➤ In tessellation(commandBuffer:), before you set the width of the compute threads with let width = min(patchCount..., add this:

```
var cameraPosition = float4(camera.position, 0)
computeEncoder.setBytes(
  &cameraPosition,
  length: MemoryLayout<float4>.stride,
  index: 3)
var matrix = modelMatrix
computeEncoder.setBytes(
  &matrix,
  length: MemoryLayout<float4x4>.stride,
  index: 4)
computeEncoder.setBuffer(
  controlPointsBuffer,
  offset: 0,
  index: 5)
computeEncoder.setBytes(
```

<a id="page-484"></a>

&amp;terrain,   length: MemoryLayout&lt;Terrain&gt;.stride,   index: 6)

You send the camera position, along with the model matrix, the control points buffer and the terrain information to the tessellation kernel.

➤ Open Tessellation.metal, and add these parameters to tessellation\_main:

```
constant float4 &camera_position [[buffer(3)]],
constant float4x4 &modelMatrix   [[buffer(4)]],
constant float3* control_points  [[buffer(5)]],
constant Terrain &terrain        [[buffer(6)]],
```

With these constants, you can compute the distance of the edges from the camera.

You’ll set the edge and inside tessellation factors differently for each patch edge instead of sending a constant 4 for all of the edges. The further the patch edge is from the camera, the lower the tessellation on that edge. These are the edge and control point orders for each patch:

![Figure](Metal_by_Tutorials_v500mpdf/3f07093b2cd040a44c1c21b4.png)

_Edges and control points_

To calculate the tessellation of an edge, you need to know the transformed mid-point of two control points. To calculate edge 2, for example, you get the midpoint of points 1 and 2 and find out the distance of that point from the camera. Where two patches join, it’s imperative to keep the tessellation level for the joined edges the same, otherwise you get cracks. By calculating the distance of the mid-point, you end up with the same result for the overlapping edges.

➤ In Tessellation.metal, create a new function before tessellation\_main:

```
float calc_distance(
  float3 pointA, float3 pointB,
  float3 camera_position,
```

<a id="page-485"></a>

```
  float4x4 modelMatrix)
{
  float3 positionA = (modelMatrix * float4(pointA, 1)).xyz;
  float3 positionB = (modelMatrix * float4(pointB, 1)).xyz;
  float3 midpoint = (positionA + positionB) * 0.5;

  float camera_distance = distance(camera_position, midpoint);
  return camera_distance;
}
```

This function takes in two points: The camera position and the model matrix. The function then finds the mid-point between the two points and calculates the distance from the camera.

➤ Remove all of the code from tessellation\_main.

➤ Add the following line of code to tessellation\_main to calculate the correct index into the tessellation factors array:

`uint index = pid * 4;`

4 is the number of control points per patch, and pid is the patch ID. To index into the control points array for each patch, you skip over four control points at a time.

➤ Add this line to keep a running total of tessellation factors:

`float totalTessellation = 0;`

➤ Add a `for` loop for each of the edges:

```
for (int i = 0; i < 4; i++) {
  int pointAIndex = i;
  int pointBIndex = i + 1;
  if (pointAIndex == 3) {
    pointBIndex = 0;
  }
  int edgeIndex = pointBIndex;
}
```

You cycle around four corners: 0, 1, 2, 3. On the first iteration, you calculate edge 1 from the mid-point of points 0 and 1. On the fourth iteration, you use points 3 and 0 to calculate edge 0.

➤ At the end of the `for` loop, call the distance calculation function:

```
float cameraDistance =
  calc_distance(
    control_points[pointAIndex + index],
```

<a id="page-486"></a>

```
    control_points[pointBIndex + index],
    camera_position.xyz,
    modelMatrix);
```

➤ Then, still inside the `for` loop, set the tessellation factor for the current edge:

```
float tessellation =
  max(4.0, terrain.maxTessellation / cameraDistance);
factors[pid].edgeTessellationFactor[edgeIndex] = tessellation;
totalTessellation += tessellation;
```

You set a minimum edge factor of 4. The maximum depends upon the camera distance and the maximum tessellation amount you specified for the terrain.

➤ After the `for` loop, add this:

```
factors[pid].insideTessellationFactor[0] =
  totalTessellation * 0.25;
factors[pid].insideTessellationFactor[1] =
  totalTessellation * 0.25;
```

You set the two inside tessellation factors to be an average of the total tessellation for the patch. You’ve now finished creating the compute kernel which calculates the edge factors based on distance from the camera.

Lastly, you’ll revise some of the default render pipeline state tessellation parameters.

➤ Open Pipelines.swift, and in createRenderPSO(), add this before the return:

```
// 1
pipelineDescriptor.tessellationFactorStepFunction = .perPatch
// 2
pipelineDescriptor.maxTessellationFactor =
Renderer.maxTessellation
// 3
pipelineDescriptor.tessellationPartitionMode = .fractionalEven
```

1. The step function was previously set to a default .constant, which sets the same edge factors on all patches. By setting this to .perPatch, the vertex function uses each patch’s edge and inside factors information in the tessellation factors array.

2. You set the maximum number of segments per patch for the tessellator.

3. The partition mode describes how these segments are split up. The default is .pow2, which rounds up to the nearest power of two. Using .fractionalEven, the tessellator rounds up to the nearest even integer, so it allows for much more variation of tessellation.

<a id="page-487"></a>

➤ Build and run the app, and rotate and zoom your patches.

As you reposition the patches, the tessellator recalculates their distance from the camera and tessellates accordingly. Tessellating is a neat superpower!

![Figure](Metal_by_Tutorials_v500mpdf/7b6dce9158f28d89e2d6dc70.png)

_Tessellation by distance_

Check where the patches join. The triangles of each side of the patch should connect.

Now that you’ve mastered tessellation, you’ll be able to add detail to your terrain.

## **Displacement**

You’ve used textures for various purposes in earlier chapters. Now you’ll use a height map to change the height of each vertex. Height maps are grayscale images where you can use the texel value for the Y vertex position, with white being high and black being low. There are several height maps in Textures.xcassets you can experiment with.

➤ Open **Renderer.swift**, and create a property to hold the height map:

`let heightMap: MTLTexture!`

➤ In init(metalView:options:), before calling super.init(), initialize heightMap:

`heightMap = TextureController.loadTexture(name: "mountain")`

Here, you load the height map texture from the asset catalog.

<a id="page-488"></a>

➤ In render(commandBuffer:view:), add the following code before the draw call renderEncoder.drawPatches(...):

```
renderEncoder.setVertexTexture(heightMap, index: 0)
renderEncoder.setVertexBytes(
  &terrain,
  length: MemoryLayout<Terrain>.stride,
  index: 6)
```

You’re already familiar with sending textures to the fragment shader, which makes the texture available to the vertex shader in the same way. You also send the terrain setup details.

➤ Open Shaders.metal, and add the following to vertex\_main’s parameters:

```
texture2d<float> heightMap [[texture(0)]],
constant Terrain &terrain [[buffer(6)]],
```

You read in the texture and terrain information.

You’re currently only using the x and z position coordinates for the patch and leaving the y coordinate as zero. You’ll now map the y coordinate to the height indicated in the texture.

Just as you used u and v fragment values to read the appropriate texel in the fragment function, you use the x and z position coordinates to read the texel from the height map in the vertex function.

➤ After setting position, but before multiplying by the model-view-projection matrix, add this:

```
// 1
float2 xy = (position.xz + terrain.size / 2.0) / terrain.size;
// 2
constexpr sampler sample;
float4 color = heightMap.sample(sample, xy);
out.color = float4(color.r);
// 3
float height = (color.r * 2 - 1) * terrain.height;
position.y = height;
```

<a id="page-489"></a>

Going through the code:

1. You convert the patch control point values to be between 0 and 1 to be able to sample the height map. You include the terrain size because, although your patch control points are currently between -1 and 1, soon you’ll be making a larger terrain.

2. Create a default sampler and read the texture as you have done previously in the fragment function. The texture is a grayscale texture, so you only use the .r value.

3. color is between 0 and 1, so for the height, shift the value to be between -1 and 1, and multiply it by your terrain height scale setting. This is currently set to 1.

➤ Next, remove the following code from the end of the vertex function, because you’re now using the color of the height map.

```
out.color = float4(0);
if (patchID == 0) {
  out.color = float4(1, 0, 0, 1);
}
```

➤ Open Renderer.swift, and change the rotation property initialization in modelMatrix to:

`let rotation = float3(Float(-20).degreesToRadians, 0, 0)`

You’ll now look at your tessellated plane from the side, rather than from the top.

➤ Build and run the app to see the height map displacing the vertices. Turn off the wireframe, and notice how the white vertices are high and the black ones are low:

![Figure](Metal_by_Tutorials_v500mpdf/83ea15978605aa2f7793a5cd.png)

_Height map displacement_

<a id="page-490"></a>

This render doesn’t yet have much detail, but that’s about to change.

➤ In **Renderer.swift**, change the `maxTessellation` constant to:

```
static var maxTessellation: Int {
  device?.supportsFamily(.apple5) ?? false ? 64 : 16
}
```

Now you’re using as much tessellation detail as currently allowed by the GPU.

➤ Change `patches` and `terrain` to:

```
let patches = (horizontal: 6, vertical: 6)
lazy var terrain = Terrain(
  size: [8, 8],
  height: 1,
  maxTessellation: UInt32(Renderer.maxTessellation))
```

This time, you’re creating thirty-six patches over sixteen units. Because maxTessellation now relies on device, you set terrain to initialize lazily.

➤ Build and run the app to see your patch height-mapped into a magnificent mountain. Don’t forget to click off the wireframe option to see your mountain render in its full glory.

![Figure](Metal_by_Tutorials_v500mpdf/3492e0887952116a9719ead7.png)

_A tessellated mountain_

Now it’s time to render your mountain with different colors and textures depending on height.

<a id="page-491"></a>

## **Shading By Height**

In the previous section, you sampled the height map in the vertex function, and the colors are interpolated when sent to the fragment function. For maximum color detail, you need to sample from textures per fragment, not per vertex.

For that to work, you’ll set up three textures: snow, cliff and grass. You’ll send these textures to the fragment function and test the height there.

➤ Open Renderer.swift, and add three new texture properties to Renderer:

```
let cliffTexture: MTLTexture?
let snowTexture: MTLTexture?
let grassTexture: MTLTexture?
```

➤ In `init(metalView:options:)`, where you create the height map, add this:

```
cliffTexture = TextureController.loadTexture(name: "cliff-
color")
snowTexture = TextureController.loadTexture(name: "snow-color")
grassTexture = TextureController.loadTexture(name: "grass-
color")
```

These textures are in the asset catalog.

➤ To send the textures to the fragment function, in render(commandBuffer:view:), add the following code before the renderEncoder draw call:

```
renderEncoder.setFragmentTexture(cliffTexture, index: 1)
renderEncoder.setFragmentTexture(snowTexture, index: 2)
renderEncoder.setFragmentTexture(grassTexture, index: 3)
```

➤ Open Shaders.metal, and add two new properties to VertexOut:

```
float height;
float2 uv;
```

➤ At the end of vertex\_main, before the return, set the value of these two properties:

```
out.uv = xy;
out.height = height;
```

You send the height value from the vertex function to the fragment function so that you can assign fragments the correct texture for that height.

<a id="page-492"></a>

➤ Add the textures to the `fragment_main` parameters:

```
texture2d<float> cliffTexture [[texture(1)]],
texture2d<float> snowTexture  [[texture(2)]],
texture2d<float> grassTexture [[texture(3)]]
```

➤ Replace the contents of `fragment_main` with:

```
constexpr sampler sample(filter::linear, address::repeat);
float tiling = 16.0;
float4 color;
if (in.height < -0.5) {
  color = grassTexture.sample(sample, in.uv * tiling);
} else if (in.height < 0.3) {
  color = cliffTexture.sample(sample, in.uv * tiling);
} else {
  color = snowTexture.sample(sample, in.uv * tiling);
}
return color;
```

You create a tileable texture sampler and read in the appropriate texture for the height. Height is between -1 and 1, as set in vertex\_main. You then tile the texture by 16 — an arbitrary value based on what looks best here.

➤ Build and run the app. Click the wireframe toggle to see your textured mountain.

You have grass at low altitudes and snowy peaks at high altitudes.

![Figure](Metal_by_Tutorials_v500mpdf/40166449987b51572178dddc.png)

_A textured mountain_

As you zoom and rotate, notice how the mountain seems to ripple. This is the tessellation level of detail being over-sensitive. One way of dialing this down is to change the render pass’s tessellation partition mode.

<a id="page-493"></a>

➤ Open Pipelines.swift, and in createRenderPSO(), change the pipelineDescriptor.tessellationPartitionMode assignment to:

`pipelineDescriptor.tessellationPartitionMode = .pow2`

➤ Build and run the app.

As the tessellator rounds up the edge factors to a power of two, there’s a larger difference in tessellation between the patches now, but the change in tessellation won’t occur so frequently, and the ripple disappears.

![Figure](Metal_by_Tutorials_v500mpdf/525da43ee2b492ca5dd8d5e3.png)

_Rounding edge factors to a power of two_

## **Shading By Slope**

The snow line in your previous render is unrealistic. By checking the slope of the mountain, you can show the snow texture in flatter areas, and show the cliff texture where the slope is steep.

An easy way to calculate slope is to run a Sobel filter on the height map. A Sobel filter is an algorithm that looks at the gradients between neighboring pixels in an image. It’s useful for edge detection in computer vision and image processing, but in this case, you can use the gradient to determine the slope between neighboring pixels.

## **Metal Performance Shaders**

The Metal Performance Shaders framework contains many useful, highly optimized shaders for image processing, matrix multiplication, machine learning and raytracing. You’ll read more about them in Chapter 29, “Metal Performance Shaders.”

<a id="page-494"></a>

The shader you’ll use here is MPSImageSobel, which takes a source image texture and outputs the filtered image into a new grayscale texture. The whiter the pixel, the steeper the slope.

Note: In the challenge for this chapter, you’ll use the Sobel-filtered image and apply the three textures to your mountain depending on slope.

➤ Open **Renderer.swift**, and import the Metal Performance Shaders framework:

`import MetalPerformanceShaders`

➤ Create a new method in `Renderer` to process the height map:

```
static func heightToSlope(source: MTLTexture) -> MTLTexture {
}
```

Next, you’ll send the height map to this method and return a new texture. To create the new texture, you first need to create a texture descriptor where you can assign the size, pixel format and tell the GPU how you will use the texture.

➤ Add this to heightToSlope(source:):

```
let descriptor =
  MTLTextureDescriptor.texture2DDescriptor(
    pixelFormat: source.pixelFormat,
    width: source.width,
    height: source.height,
    mipmapped: false)
descriptor.usage = [.shaderWrite, .shaderRead]
```

You create a descriptor for textures that you want to both read and write. You’ll write to the texture in the MPS shader and read it in the fragment shader.

➤ Continue adding to the method:

```
guard let destination =
  Renderer.device.makeTexture(descriptor: descriptor),
  let commandBuffer = Renderer.commandQueue.makeCommandBuffer()
else {
  fatalError("Error creating Sobel texture")
}
```

This creates the texture and the command buffer for the MPS shader.

<a id="page-495"></a>

➤ Now, add this:

```
let shader = MPSImageSobel(device: Renderer.device)
shader.encode(
  commandBuffer: commandBuffer,
  sourceTexture: source,
  destinationTexture: destination)
commandBuffer.commit()
return destination
```

You run the MPS shader and return the texture. That’s all there is to running a Metal Performance Shader on a texture.

Note: The height maps in the asset catalog have a pixel format of 8 Bit Normalized - R, or R8Unorm. Using the Automatic pixel format with MPSImageSobel crashes. In any case, for grayscale texture maps that only use one channel, using R8Unorm as a pixel format is more efficient.

➤ To hold the terrain slope in a texture, add a new property to Renderer:

`let terrainSlope: MTLTexture`

➤ In init(metalView:options:), before calling super.init(), initialize the texture:

`terrainSlope = Renderer.heightToSlope(source: heightMap)`

<a id="page-496"></a>

The texture when created will look like this:

![Figure](Metal_by_Tutorials_v500mpdf/a0be6abb6d885da2ed3ffa58.png)

_The Sobel filter (contrast enhanced)_

In the challenge, once you send this texture to the vertex shader, you’ll be able to see it using the Capture GPU Frame icon. The red parts are the steep slopes.

## **Challenge**

Your challenge for this chapter is to use the slope texture from the Sobel filter to place snow on the mountain on the parts that aren’t steep. Because you don’t need pixel perfect accuracy, you can read the slope image in the vertex function and send that value to the fragment function. This is more efficient as there will be fewer texture reads in the vertex function than in the fragment function.

If everything goes well, you’ll render an image like this:

![Figure](Metal_by_Tutorials_v500mpdf/2c515289c7d4ea87a7097626.png)

_Shading by slope_

<a id="page-497"></a>

Notice how the grass blends into the mountain. This is done using the mix() function.

Currently, you have three zones — the heights where you render the three different textures. The challenge project has four zones:

• grass: &lt; -0.6 in height

• grass blended with mountain: -0.6 to -0.4

• mountain: -0.4 to -0.2

• mountain with snow on the flat parts: &gt; -0.2

See if you can get your mountain to look like the challenge project in the projects directory for this chapter.

<a id="page-498"></a>

## **Key Points**

• Tessellation utilizes specialized hardware units on the GPU to create extra vertices.

• You send patches to the GPU rather than vertices. The tessellator then breaks down these patches to smaller triangles.

• A patch can be either a triangle or a quad.

• The tessellation pipeline has an extra stage of setting edge and inside factors in a tessellation kernel. These factors decide the number of vertices that the tessellator should create.

• The vertex shader handles the vertices created by the tessellator.

• Vertex displacement uses a grayscale texture to move the vertex, generally in the y direction.

• The Sobel Metal Performance Shader takes a texture and generates a new texture that defines the slope of a pixel.

<a id="page-499"></a>

## **Where to Go From Here?**

With very steep displacement, there can be lots of texture stretching between vertices. There are various algorithms to overcome this, and you can find one in Apple’s excellent sample code: Rendering Terrain Dynamically with Argument Buffers (https://developer.apple.com/documentation/metal/ fundamental\_components/gpu\_resources/dynamic\_terrain\_with\_argument\_buffers). This is a complex project that showcases argument buffers, but the dynamic terrain portion is interesting.

There’s another way to do blending. Instead of using mix(), the way you did in the challenge, you can use a texture map to define the different regions. This is known as texture splatting. You create a splat map with the red, blue and green channels describing up to three textures and where to use them.

![Figure](Metal_by_Tutorials_v500mpdf/d900add5635c84186e818608.png)

_A splat map_

With all of the techniques for reading and using textures that you’ve learned so far, texture splatting shouldn’t be too difficult for you to implement.

<a id="page-500"></a>

# 20

# Chapter 20: Fragment Post-Processing

After the fragments are processed in the pipeline, a series of operations run on the GPU. These operations are sometimes referred to as Per-sample Processing (https:// www.khronos.org/opengl/wiki/Per-Sample\_Processing) and include: alpha testing, depth testing, stencil testing, scissor testing, blending and anti-aliasing. You’ve already encountered a few of these operations in earlier chapters, such as depth testing and stencil testing. Now it’s time to revisit those concepts while also learning about the others.

<a id="page-501"></a>

## **The Starter App**

➤ In Xcode, open the starter app for this chapter, and build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/edb1c4c1da2f8e6bd353b5f3.png)

_The starter app_

The standard forward renderer renders the scene containing a ground plane and a tree. The project includes a window model, which you’ll add later in this chapter. You can use the options at the top-left of the screen to toggle the post-processing effects. Those effects aren’t active yet, but they will be soon!

Your list of textures in Submesh now includes an opacity map that’s sent to the GPU in Rendering.swift. Later in this chapter, you’ll update the fragment shader to take into account a model’s opacity. If you need help adding texture types to your renderer, review Chapter 11, “Maps &amp; Materials”.

## **Using Booleans in a C Header File**

In Renderer.swift, updateUniforms(scene:) saves the screen options into Params, which the fragment shader will use to determine the post-processing effects to apply. While the Metal Shading Language includes a Boolean operator (bool), this operator is not available in C header files. In the Shaders folder included with this starter project, is stdbool.h. This file defines a bool, which Common.h imports. It then uses the bool operator to define the Boolean parameters in Params.

<a id="page-502"></a>

## **Alpha Testing**

Move closer to the tree using the scroll wheel or the two-finger gesture on your trackpad, and you’ll notice the leaves look a little odd.

![Figure](Metal_by_Tutorials_v500mpdf/e778b7af9696b7a7949719b5.png)

_Opaque edge around leaves_

The base color texture in **tree.usdz** looks like this:

![Figure](Metal_by_Tutorials_v500mpdf/7c7f1da93e57d69bf80081f0.png)

_Tree-color texture_

The area of the texture surrounding the leaf is transparent, yet it renders as either white or black, depending on the device.

To make the leaves look more natural, you’ll render the transparent part of the texture as transparent in the scene. However, before making this change, it’s important to understand the difference between transparent, translucent, and opaque objects.

A transparent object allows light to entirely pass through it. A translucent object distorts light as it passes through it. An opaque object does not allow any light to pass through it. Most objects in nature are opaque. Objects like water, glass and plastic are translucent.

<a id="page-503"></a>

Digital colors are formed using a combination of the three primary colors: red, green and blue — hence the color scheme RGB. However, there’s a fourth component you can add to the color definition: alpha. Alpha ranges from 0 (fully transparent) to 1 (fully opaque). A common practice in determining transparency is to check the alpha property and ignore values below a certain threshold. This technique is known as alpha testing.

➤ Open Fragment.metal. In fragment\_main, locate the conditional closure where you set material.baseColor.

➤ Replace the contents of `if (!is_null_texture(baseColorTexture)) {}` with:

```
float4 color = baseColorTexture.sample(
  textureSampler,
  in.uv * params.tiling);
if (params.alphaTesting && color.a < 0.1) {
  discard_fragment();
  return 0;
}
material.baseColor = color.rgb;
```

With this change, you now read in the alpha value of the color as well as the RGB values. If the alpha is less than a 0.1 threshold, and you’re performing alpha testing, then you discard the fragment. The GPU ignores the returned 0 and stops processing the fragment.

➤ Build and run the app, and toggle **Alpha Testing** to see the difference.

![Figure](Metal_by_Tutorials_v500mpdf/a47771e934d32feca27a7b47.png)

_Alpha testing_

That’s much better! Now, when you get closer to the tree, you’ll notice the extra edging around the leaves is gone.

<a id="page-504"></a>

## **Depth Testing**

Depth testing compares the depth value of the current fragment to one stored in the framebuffer. If a fragment is farther away than the current depth value, this fragment fails the depth test and is discarded since it’s occluded by another fragment. You learned about depth testing in Chapter 7, “The Fragment Function”.

## **Stencil Testing**

Stencil testing compares the value stored in a stencil attachment to a masked reference value. If a fragment makes it through the mask it’s kept, otherwise it’s discarded. You learned about stencil testing in Chapter 15, “Tile-Based Deferred Rendering”.

## **Scissor Testing**

If you only want to render part of the screen, you can tell the GPU to render only within a particular rectangle. This is much more efficient than rendering the entire screen. The scissor test checks whether a fragment is inside a defined 2D area known as the scissor rectangle. If the fragment falls outside of this rectangle, it’s discarded.

➤ Open ForwardRenderPass.swift, which is where you set up your render command encoder to draw the models.

➤ In draw(commandBuffer:scene:uniforms:params:), before for model in scene.models, add this:

```
if params.scissorTesting {
  let marginWidth = Int(params.width) / 4
  let marginHeight = Int(params.height) / 4
  let width = Int(params.width) / 2
  let height = Int(params.height) / 2
  let rect = MTLScissorRect(
    x: marginWidth, y: marginHeight, width: width, height:
height)
  renderEncoder.setScissorRect(rect)
}
```

Here, you set the scissor rectangle to half the width and height of the current metal view.

<a id="page-505"></a>

➤ Build and run the app, and turn on Scissor Testing.

![Figure](Metal_by_Tutorials_v500mpdf/ea3aada8905d7b6d94a822af.png)

_Scissor testing_

Keep in mind that any objects rendered before you set the scissor rectangle are not affected. This means that you can choose to render within a scissor rectangle only for selected models.

## **Alpha Blending**

Alpha blending is different from alpha testing in that the latter only works with total transparency. In that case, all you have to do is discard fragments. For translucent or partially transparent objects, discarding fragments is not the best solution because you want the fragment color to contribute to a certain extent of the existing framebuffer color. You don’t just want to replace it. You had a taste of blending in Chapter 14, “Deferred Rendering”, when you blended the result of your point lights.

The formula for alpha blending is as follows:

![Figure](Metal_by_Tutorials_v500mpdf/33fb191c17d05d07f4249363.png)

Going over this formula:

• Cs: Source color. The current color you just added to the scene.

• Cd: Destination color. The color that already exists in the framebuffer.

• Cb:  Final blended color.

• ⍺1 and ⍺2: The alpha (opacity) factors for the source and destination color, respectively.

<a id="page-506"></a>

The final blended color is the result of adding the products between the two colors and their opacity factors. The source color is the fragment color you put in front, and the destination color is the color already existing in the framebuffer.

Often the two factors are the inverse of each other transforming this equation into linear color interpolation:

![Figure](Metal_by_Tutorials_v500mpdf/2971462ed56639b38e293a21.png)

All right, time to install a glass window in front of the tree.

➤ Open GameScene.swift. In init(), change models = [ground, tree] to:

```
window.position = [0, 3, -1]
models = [window, ground, tree]
```

➤ Build and run the app, and you’ll see the window:

![Figure](Metal_by_Tutorials_v500mpdf/48ed10cd9fa27ca030d17bc4.png)

_The window in the scene_

You can’t yet view the tree through the window, but you’ll fix that with blending. There are two ways to work with blending: the programmable way and the fixed-function way. You used programmable blending with color attachments in Chapter 15, “Tile-Based Deferred Rendering”. In this chapter, you’ll use fixed-function blending.

<a id="page-507"></a>

## **Opacity**

To define transparency in models, you either create a grayscale texture known as an opacity map, or you define opacity in the submesh’s material. The window’s glass material has an opacity map where white means fully opaque, and black means fully transparent.

![Figure](Metal_by_Tutorials_v500mpdf/256b3f67e2ff66819619c305.png)

_The window's opacity map_

## **Blending**

To implement blending, you need a second pipeline state in your render pass. You’ll still use the same shader functions, but you’ll turn on blending in the GPU.

➤ Open **Pipelines.swift**, and copy `createForwardPSO()` to a new method.

➤ Rename the new method to createForwardTransparentPSO().

➤ In createForwardTransparentPSO(), after setting pipelineDescriptor.colorAttachments[0].pixelFormat, add this:

```
// 1
let attachment = pipelineDescriptor.colorAttachments[0]
// 2
attachment?.isBlendingEnabled = true
// 3
attachment?.rgbBlendOperation = .add
// 4
attachment?.sourceRGBBlendFactor = .sourceAlpha
```

<a id="page-508"></a>

```
// 5
attachment?.destinationRGBBlendFactor = .oneMinusSourceAlpha
```

With this code, you:

1. Grab the first color attachment from the render pipeline descriptor. The color attachment is a color render target that specifies the color configuration and color operations associated with a render pipeline. The render target holds the drawable texture where the rendering output goes.

2. Enable blending on the attachment.

3. Specify the blending type of operation used for color. Blend operations determine how a source fragment is combined with a destination value in a color attachment to determine the pixel value to be written.

4. Specify the blend factor used by the source color. A blend factor is how much the color will contribute to the final blended color. If not specified, this value is always 1 (.one) by default.

5. Specify the blend factor used by the destination color. If not specified, this value is always 0 (.zero) by default.

Note: There are quite a few blend factors available to use other than sourceAlpha and oneMinusSourceAlpha. For a complete list of options, consult Apple’s official page for Blend Factors (https://developer.apple.com/ documentation/metal/mtlblendfactor).

➤ Open ForwardRenderPass.swift, and add a new property to ForwardRenderPass:

`var transparentPSO: MTLRenderPipelineState`

➤ In `init(view:)`, add this:

`transparentPSO = PipelineStates.createForwardTransparentPSO()`

You initialized the new pipeline state object with your new pipeline creation method.

➤ In draw(commandBuffer:scene:uniforms:params:), replace renderEncoder.setRenderPipelineState(pipelineState) with:

`renderEncoder.setRenderPipelineState(transparentPSO)`

<a id="page-509"></a>

You temporarily replace the pipeline state with your new one. Blending is always enabled now.

➤ Open Fragment.metal. In fragment\_main, after the conditional where you set material.baseColor, add this:

```
if (params.alphaBlending) {
  if (!is_null_texture(opacityTexture)) {
    material.opacity =
      opacityTexture.sample(textureSampler, in.uv).r;
  }
}
```

If you have the alpha blending option turned on, read the value from a provided opacity texture. If no texture is provided, you’ll use the default from material, loaded with the model’s submesh.

➤ At the end of `fragment_main`, replace the return value with:

`return float4(diffuseColor + specularColor, material.opacity);`

You return the opacity value in the alpha channel.

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/0776257c9a094e352bee0bc9.png)

_Opacity not working_

Even though you’ve set blending in the pipeline state and changed the opacity in the fragment function, the opacity doesn’t appear to be working. The glass has changed color from the previous render. This indicates that the transparency is actually working. It’s showing the view’s clear color through the glass, rather than the tree and the ground.

<a id="page-510"></a>

➤ Open GameScene.swift. In init(), change models = [window, ground, tree] to:

`models = [ground, tree, window]`

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/93fb68852e3e1937efab947c.png)

_Opacity is working_

The opacity is working. If you zoom in, you can see the weathering on the old glass. This is achieved by varying the opacity grayscale values in the texture.

Note: Remember if you want to examine textures, you can use GPU Frame Capture to see what the GPU is processing.

## **Transparent Mesh Rendering Order**

The blending order is important. Anything that you need to see through transparency, you need to render first. However, it may not always be convenient to work out exactly which models require blending. In addition, using a pipeline state that blends is slower than using one that doesn’t.

➤ Undo the previous change to `models` so that you render the window first again.

First set up your models to indicate whether any of the submeshes aren’t opaque.

➤ Open Submesh.swift, and add a computed property to Submesh:

```
var transparency: Bool {
  return textures.opacity != nil || material.opacity < 1.0
}
```

<a id="page-511"></a>

`transparency` is true if the submesh textures or material indicate transparency.

➤ Open **Model.swift**, and add a new property:

`var hasTransparency = false`

To initialize this property, you’ll process all of the model’s submeshes, and if any of them have transparency set to true, then the model is not fully opaque.

➤ At the end of `init(name:)`, add this:

```
hasTransparency = meshes.contains { mesh in
  mesh.submeshes.contains { $0.transparency }
}
```

If any of the model’s submeshes have transparency, you’ll process the model during the transparency render phase.

➤ Open Rendering.swift. In render(encoder:uniforms:params:), locate for submesh in mesh.submeshes.

➤ At the top of the `for` loop, add this:

`if submesh.transparency != params.transparency { continue }`

You only render the submesh if its transparency matches the current transparency in the render loop.

➤ Open Common.h, and add a new property to Params:

`bool transparency;`

You’ll use this property to track when you’re currently rendering transparent submeshes.

➤ Open ForwardRenderPass.swift. In draw(commandBuffer:scene:uniforms:params:), change the pipeline state back to what it was originally:

`renderEncoder.setRenderPipelineState(pipelineState)`

➤ Locate for model in scene.models. Before the for loop, add this:

```
var params = params
params.transparency = false
```

<a id="page-512"></a>

In the render loop, you’ll only render submeshes with no transparency.

➤ Now, before `renderEncoder.endEncoding()`, add this:

```
// transparent mesh
renderEncoder.pushDebugGroup("Transparency")
let models = scene.models.filter {
  $0.hasTransparency
}
params.transparency = true
if params.alphaBlending {
  renderEncoder.setRenderPipelineState(transparentPSO)
}
for model in models {
  model.render(
    encoder: renderEncoder,
    uniforms: uniforms,
    params: params)
}
renderEncoder.popDebugGroup()
```

Here, you filter the scene models array to find only those models that have a transparent submesh. You then change the pipeline state to use alpha blending, and render the filtered models.

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/b7d80965f43839f06a72c041.png)

_Alpha blending_

You can now see through your window.

<a id="page-513"></a>

Note: If you have several transparent meshes overlaying each other, you’ll need to sort them to ensure that you render them in strict order from back to front.

➤ In the app, turn off Alpha Blending.

At the end of the render loop, the pipeline state doesn’t switch to the blending one, so the window becomes opaque again.

![Figure](Metal_by_Tutorials_v500mpdf/5b220fd925a4bc9148daae6d.png)

_Alpha blending turned off_

## **Antialiasing**

Often, rendered models show slightly jagged edges that are visible when you zoom in. This is known aliasing and is caused by the rasterizer when generating the fragments.

![Figure](Metal_by_Tutorials_v500mpdf/096fcd6b1d8948c5e25a7c25.png)

_Rasterizing a triangle_

<a id="page-514"></a>

If you look at the edges of a triangle — or any straight line with a slope — you’ll notice the line doesn’t always go precisely through the center of a pixel. Some pixels are colored above the line and some below it. The solution to fixing aliasing is to use antialiasing. Antialiasing applies techniques to render smoother edges.

By default, the pipeline uses one sample point (subpixel) for each pixel that is close to the line to determine if they meet. However, it’s possible to use four or more points for increased accuracy of intersection determination. This is known as Multisample Antialiasing (MSAA), and it’s more expensive to compute.

Next, you’re going to configure the fixed-function MSAA on the pipeline and enable antialiasing on both the tree and the window.

➤ Open Pipelines.swift, and duplicate both createForwardPSO() and createForwardTransparentPSO().

➤ Name them createForwardPSO\_MSAA() and createForwardTransparentPSO\_MSAA(), respectively.

➤ In both new methods, before the return, add this:

`pipelineDescriptor.rasterSampleCount = 4`

➤ Open **ForwardRenderPass.swift**, and add two new properties:

```
var pipelineStateMSAA: MTLRenderPipelineState
var transparentPSOMSAA: MTLRenderPipelineState
```

➤ In init(), initialize the new pipeline states with your new pipeline state creation methods:

```
pipelineStateMSAA = PipelineStates.createForwardPSO_MSAA()
transparentPSOMSAA =
  PipelineStates.createForwardTransparentPSO_MSAA()
```

➤ At the top of `draw(commandBuffer:scene:uniforms:params:)`, add this:

```
let pipelineState = params.antialiasing ?
  pipelineStateMSAA : pipelineState
let transparentPSO = params.antialiasing ?
  transparentPSOMSAA : transparentPSO
```

<a id="page-515"></a>

Depending upon whether the user has selected Antialiasing, you set the different pipeline state.

The render target texture must match the same sample count as the pipeline state.

➤ Open Renderer.swift, and at the top of draw(scene:in:) before the guard, add this:

`view.sampleCount = options.antialiasing ? 4 : 1`

The current render pass descriptor will use the sample count to create the render target texture with the correct antialiasing.

➤ Build and run the app. On modern retina devices, this effect can be quite difficult to see. But, if you zoom in to a straight line on a slope — such as the tree trunk or the top of the window — and toggle Antialiasing, you may notice the difference.

![Figure](Metal_by_Tutorials_v500mpdf/fbaf186c3a7b569a653acf3a.png)

_Antialiasing_

<a id="page-516"></a>

## **Fog**

Let’s have a bit more fun and add some fog to the scene!

Fog is useful in rendering for a couple of reasons. First, it serves as a far delimiter for rendered content. The renderer can ignore objects that get lost in the fog since they’re not visible anymore. Second, fog helps you avoid the popping-up effect that can happen when objects that are farther away from the camera “pop” into the scene as the camera moves closer. With fog, you can make their appearance into the scene more gradual.

Note: Fog isn’t a post-processing effect, it’s added in the fragment shader.

➤ Open Fragment.metal, and add a new function before fragment\_main:

```
float4 fog(float4 position, float4 color) {
  // 1
  float distance = position.z / position.w;
  // 2
  float density = 0.1;
  float fog = 1.0 - clamp(exp(-density * distance), 0.0, 1.0);
  // 3
  float4 fogColor = float4(1.0);
  color = mix(color, fogColor, fog);
  return color;
}
```

With this code, you:

1. Calculate the depth of the fragment position.

2. Define a distribution function that the fog will use next. It’s the inverse of the clamped (between 0 and 1) product between the fog density and the depth calculated in the previous step.

3. Mix the current color with the fog color (which you deliberately set to white) using the distribution function defined in the previous step.

<a id="page-517"></a>

➤ Change the return value of `fragment_main` to:

```
float4 color =
  float4(diffuseColor + specularColor, material.opacity);
if (params.fog) {
  color = fog(in.position, color);
}
return color;
```

Here, you include the fog value in the final color.

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/c5b9b6aa7d2a862162863021.png)

_Fog_

Perfect, the entire scene is foggy. The closer you get to the tree, the less dense the fog. The same happens to the ground. Like with real fog, the closer you get to an object, the easier it is to see it. Check it out: get closer to the tree, and you’ll see it a lot better.

Because this effect is worked in the fragment shader, the sky is not affected by fog. The sky color is coming from the MTKView instead of being rendered. In the next chapter, you’ll create a rendered sky that you can affect with fog.

<a id="page-518"></a>

## **Key Points**

• Per-sample processing takes place in the GPU pipeline after the GPU processes fragments.

• Using discard\_fragment() in the fragment function halts further processing on the fragment.

• To render only part of the texture, you can define a 2D scissor rectangle. The GPU discards any fragments outside of this rectangle.

• You set up the pipeline state object with blending when you require transparency. You can then set the alpha value of the fragment in the fragment function. Without blending in the pipeline state object, all fragments are fully opaque, no matter their alpha value.

• Multisample antialiasing improves render quality. You set up MSAA with the sampleCount in the pipeline state descriptor.

• You can add fog with some clever distance shading in the fragment function.

## **Where to Go From Here?**

Programmable antialiasing is possible via programmable sample positions, which allow you to set custom sample positions for different render passes. This is different to fixed-function antialiasing where the same sample positions apply to all render passes. For further reading, you can review Apple’s Positioning Samples Programmatically (https://developer.apple.com/documentation/metal/ mtlrenderpassdescriptor/positioning\_samples\_programmatically) article.

<a id="page-519"></a>

# 21

# Chapter 21: Image-Based Lighting

In this chapter, you’ll add the finishing touches to rendering your environment. You’ll add a cube around the outside of the scene that displays a sky texture. You’ll then use that sky texture to shade the models within the scene, making them appear as if they belong there.

Look at the following comparison of two renders.

![Figure](Metal_by_Tutorials_v500mpdf/2e0109103b912377e85a14d1.png)

_The final and challenge renders_

This comparison demonstrates how you can use the same shader code but change the sky image to create different lighting environments. The rendered models reflect the tinge of color from the sky.

<a id="page-520"></a>

## **The Starter Project**

➤ In Xcode, open the starter project for this chapter and build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/5b80987067e0f4f033ca5509.png)

_The starter project_

The project contains the forward renderer with transparency from the previous chapter. The scene uses an arcball camera, and contains a ground plane and car. The scene lighting consists of one sunlight.

There are a few additional files that you’ll use throughout the chapter. Common.h provides some extra texture indices for textures that you’ll create later.

There are some glaring problems with the render:

• All metals, such as the metallic wheel hubs, look dull. Pure metals reflect their surroundings, and there are currently no surroundings to reflect.

• Where the light doesn’t directly hit the car, the color is pure black. This happens because the app doesn’t provide any ambient light. Later in this chapter, you’ll use the skylight as global ambient light.

## **The Skybox**

Currently, the sky is a single color, which looks unrealistic. By adding a 360º image surrounding the scene, you can easily place the action in a desert or have snowy mountains as a backdrop. To do this, you’ll create a skybox cube that surrounds the entire scene.

<a id="page-521"></a>

This skybox cube is the same as an ordinary model, but instead of viewing it from the outside, the camera is at the center of the cube looking out. You’ll texture the cube with a cube texture, which gives you a cheap way of creating a complete environment.

You may think the cube will be distorted at the corners, but as you’ll see, each fragment of the cube will render at an effectively infinite distance, and no distortion will occur. Cube maps are much easier to create than spherical ones and are hardware optimized.

➤ In the Geometry folder, create a new Swift file for the skybox class named Skybox.swift.

➤ Replace the default code with:

```
import MetalKit

struct Skybox {
  let mesh: MTKMesh
  var skyTexture: MTLTexture?
  let pipelineState: MTLRenderPipelineState
  let depthStencilState: MTLDepthStencilState?
}
```

Going through the skybox properties:

• mesh: A cube that you’ll create using a Model I/O primitive.

• skyTexture: A cube texture of the name given in the initializer. This is the texture that you’ll see in the background.

• pipelineState: The skybox needs a simple vertex and fragment function, therefore it needs its own pipeline.

• depthStencilState: Each pixel of the skybox will be positioned at the very edge of normalized clip space. The default depth stencil state in RenderPass.swift renders the fragment if the fragment is less than the current depth value. The skybox depth stencil should test less than or equal to the current depth value. You’ll see why shortly.

Your project won’t compile until you’ve initialized all stored properties.

➤ Add the initializer to Skybox:

```
init(textureName: String?) {
  let allocator =
    MTKMeshBufferAllocator(device: Renderer.device)
```

<a id="page-522"></a>

```
  let cube = MDLMesh(
    boxWithExtent: [1, 1, 1],
    segments: [1, 1, 1],
    inwardNormals: true,
    geometryType: .triangles,
    allocator: allocator)
  do {
    mesh = try MTKMesh(
      mesh: cube, device: Renderer.device)
  } catch {
    fatalError("failed to create skybox mesh")
  }
}
```

Here, you create a cube mesh. Notice that you set the normals to face inwards. You do this because the entire scene will appear to be inside the cube.

➤ In the **Render Passes** folder, open **Pipelines.swift**, and add a new method:

```
static func createSkyboxPSO(
  vertexDescriptor: MTLVertexDescriptor?
) -> MTLRenderPipelineState {
  let vertexFunction =
    Renderer.library?.makeFunction(name: "vertex_skybox")
  let fragmentFunction =
    Renderer.library?.makeFunction(name: "fragment_skybox")
  let pipelineDescriptor = MTLRenderPipelineDescriptor()
  pipelineDescriptor.vertexFunction = vertexFunction
  pipelineDescriptor.fragmentFunction = fragmentFunction
  pipelineDescriptor.colorAttachments[0].pixelFormat =
    Renderer.viewColorPixelFormat
  pipelineDescriptor.depthAttachmentPixelFormat =
    Renderer.viewDepthPixelFormat
  pipelineDescriptor.vertexDescriptor = vertexDescriptor
  return createPSO(descriptor: pipelineDescriptor)
}
```

When you create the pipeline state, you’ll pass in the skybox cube’s Model I/O vertex descriptor. You’ll write the two new shader functions shortly.

➤ Open **Skybox.swift**, and add a new method to create the depth stencil state:

```
static func buildDepthStencilState() -> MTLDepthStencilState? {
  let descriptor = MTLDepthStencilDescriptor()
  descriptor.depthCompareFunction = .lessEqual
  descriptor.isDepthWriteEnabled = true
  return Renderer.device.makeDepthStencilState(
    descriptor: descriptor)
}
```

<a id="page-523"></a>

This creates the depth stencil state with the less than or equal comparison method mentioned earlier.

➤ Complete the initialization by adding the following code to the end of init(textureName:):

```
pipelineState = PipelineStates.createSkyboxPSO(
  vertexDescriptor: MTKMetalVertexDescriptorFromModelIO(
    cube.vertexDescriptor))
depthStencilState = Self.buildDepthStencilState()
```

You initialize the skybox’s pipeline state with the vertex descriptor provided by Model I/O.

## **Rendering the Skybox**

➤ Still in **Skybox.swift**, create a new method to perform the skybox rendering:

```
func render(
  encoder: MTLRenderCommandEncoder,
  uniforms: Uniforms
) {
  encoder.pushDebugGroup("Skybox")
  encoder.setRenderPipelineState(pipelineState)
  // encoder.setDepthStencilState(depthStencilState)
  encoder.setVertexBuffer(
    mesh.vertexBuffers[0].buffer,
    offset: 0,
    index: 0)
}
```

Here, you set up the render command encoder with the properties you initialized. Leave the depth stencil state line commented out for the moment.

➤ Add this code at the end of render(encoder:uniforms:):

```
var uniforms = uniforms
uniforms.viewMatrix.columns.3 = [0, 0, 0, 1]
encoder.setVertexBytes(
  &uniforms,
  length: MemoryLayout<Uniforms>.stride,
  index: UniformsBuffer.index)
```

When you render a scene, you multiply each model’s matrix with the view matrix and the projection matrix. As you move through the scene, it appears as if the camera is moving through the scene, but in fact, the whole scene is moving around the camera.

<a id="page-524"></a>

You don’t want the skybox to move, so you zero out column 3 of viewMatrix to remove the camera’s translation.

However, you do still want the skybox to rotate with the rest of the scene, and also render with projection, so you send the uniform matrices to the GPU.

➤ Add the following after the code you just added:

```
let submesh = mesh.submeshes[0]
encoder.drawIndexedPrimitives(
  type: .triangle,
  indexCount: submesh.indexCount,
  indexType: submesh.indexType,
  indexBuffer: submesh.indexBuffer.buffer,
  indexBufferOffset: 0)
encoder.popDebugGroup()
```

Here, you draw the cube’s submesh.

## **The Skybox Shader Functions**

In the Shaders folder, create a new Metal file named Skybox.metal.

➤ Add the following code to the new file:

```
#import "Common.h"

struct VertexIn {
  float4 position [[attribute(Position)]];
};

struct VertexOut {
  float4 position [[position]];
};
```

The structures are simple so far — you need a position in and a position out.

➤ Add the shader functions:

```
vertex VertexOut vertex_skybox(
  const VertexIn in [[stage_in]],
  constant Uniforms &uniforms [[buffer(UniformsBuffer)]])
{
  VertexOut out;
  float4x4 vp = uniforms.projectionMatrix * uniforms.viewMatrix;
  out.position = (vp * in.position).xyww;
  return out;
}
```

<a id="page-525"></a>

```
fragment half4 fragment_skybox(
  VertexOut in [[stage_in]]) {
  return half4(1, 1, 0, 1);
}
```

Here, you create two very simple shaders — the vertex function moves the vertices to the projected position, and the fragment function returns yellow. This is a temporary color, which is startling enough that you’ll be able to see where the skybox renders.

Notice in the vertex function that you swizzled the xyzw position to xyww. To place the sky as far away as possible, it needs to be at the very edge of NDC.

During the change from clip space to NDC, the coordinates are all divided by w during the perspective divide stage. This will now result in the z coordinate being 1, which will ensure that the skybox renders behind everything else within the scene.

The following diagram shows the skybox in camera space rotated by 45º. After projection and the perspective divide, the vertices will be flat against the far NDC plane.

![Figure](Metal_by_Tutorials_v500mpdf/4186ea844c927bc9dcd02525.png)

_Skybox Projection_

## **Integrating the Skybox Into the Scene**

➤ Open GameScene.swift, and add a new property to GameScene:

`let skybox: Skybox?`

➤ Add the following code to the top of init():

`skybox = Skybox(textureName: nil)`

<a id="page-526"></a>

You haven’t written the code for the skybox texture yet, but soon you’ll set it up so that nil will generate a physically simulated sky, and providing a texture name will load that sky texture.

➤ In the Render Passes folder, open ForwardRenderPass.swift, and in draw(commandBuffer:scene:uniforms:params:), locate // transparent mesh.

➤ Add the following code _before_ that comment:

```
scene.skybox?.render(
  encoder: renderEncoder,
  uniforms: uniforms)
```

You render the skybox only during the opaque pass, after the opaque meshes.

It may seem odd that you’re rendering the skybox after rendering the scene models, when it’s going to be the object that’s behind everything else. Remember early-Z testing from Chapter 3, “The Rendering Pipeline”: when objects are rendered, most of the skybox fragments will be behind them and will fail the depth test. Therefore, it’s more efficient to render the skybox as late as possible. You have to render before the transparent pass, so that any transparency will include the skybox texture.

You’ve now integrated the skybox into the rendering process.

➤ Build and run the app to see the new yellow sky.

![Figure](Metal_by_Tutorials_v500mpdf/aecc2db72f3e94351a096241.png)

_A flickering sky_

<a id="page-527"></a>

As you rotate the scene, the yellow sky flickers and shows the blue of the metal view’s clear color. This happens because the current depth stencil state is from ForwardRenderPass, and it’s comparing new fragments to less than the current depth buffer. The skybox coordinates are right on the edge, so sometimes they’re equal to the edge of clip space.

➤ Open Skybox.swift, and in render(encoder:uniforms:), uncomment encoder.setDepthStencilState(depthStencilState), and build and run the app again.

This time, the depth comparison is correct, and the sky is the solid yellow returned from the skybox fragment shader.

![Figure](Metal_by_Tutorials_v500mpdf/ed24cf597285a91f744b0769.png)

_A yellow sky_

## **Procedural Skies**

Yellow skies might be appropriate on a different planet, but how about a procedural sky? A procedural sky is one built out of various parameters such as weather conditions and time of day. Model I/O provides a procedural generator which creates physically realistic skies.

➤ Before exploring this API further, open and run the ProceduralSky app in the resources/Sky Projects folder for this chapter.

This scene contains only a ground plane and a skybox. Use your mouse or trackpad to reorient the scene. The backface of the plane will disappear if you rotate beneath it so that you can examine the sky.

<a id="page-528"></a>

Experiment with the sliders under the view to see how you can change the sky depending on:

• turbidity: Haze in the sky. 0.0 is a clear sky. 1.0 spreads the sun’s color.

• sun elevation: How high the sun is in the sky. 0.5 is on the horizon. 1.0 is overhead.

• upper atmosphere scattering: Atmospheric scattering influences the color of the sky from reddish through orange tones to the sky at midday.

• ground albedo: How clear the sky is. 0 is clear, while 10 can produce intense colors. It’s best to keep turbidity and upper atmosphere scattering low if you have high albedo.

See if you can create a sunrise:

![Figure](Metal_by_Tutorials_v500mpdf/b57793f430a41a64ac33687d.png)

_A sunrise_

This app uses Model I/O to create an MDLSkyCubeTexture. From this, the app creates an MTLTexture and applies this as a cube texture to the sky cube. You’ll now do this in your project.

<a id="page-529"></a>

## **Cube Textures**

Cube textures are similar to the 2D textures that you’ve already been using. 2D textures map to a quad and have two texture coordinates, whereas cube textures consist of six 2D textures: one for each face of the cube. You sample the textures with a 3D vector.

The easiest way to load a cube texture into Metal is to use Model I/O’s MDLTexture initializer. When creating cube textures, you can arrange the images in various combinations:

![Figure](Metal_by_Tutorials_v500mpdf/670c36c01505429d6cb5a5aa.png)

Your project’s Textures folder contains cube-sky.png and irradiance.png which are examples that you’ll load later.

Alternatively, you can create a cube texture in an asset catalog and load the six images there.

➤ Back in your project, in the Textures folder, open Textures.xcassets. sky is a sky texture complete with mipmaps.

The sky should always render on the base mipmap level 0, but you’ll see later why you would use the other mipmaps.

<a id="page-530"></a>

Aside from there being six images to one texture, moving the images into the asset catalog and creating the mipmaps is the same process as described in Chapter 8, “Textures”.

![Figure](Metal_by_Tutorials_v500mpdf/a88f4a56776d847cb3d037c4.png)

_The sky texture in the asset catalog_

## **Adding the Procedural Sky**

You’ll use these sky textures shortly, but for now, you’ll add a procedural sky to your scene.

➤ Open Skybox.swift, and add these properties to Skybox:

```
struct SkySettings {
  var turbidity: Float = 0.15
  var sunElevation: Float = 0.56
  var upperAtmosphereScattering: Float = 0.66
  var groundAlbedo: Float = 0.8
}
var skySettings = SkySettings()
```

You can use your own values from the appropriate sliders in the ProceduralSky app if you prefer.

➤ Now, add the following method:

```
func loadGeneratedSkyboxTexture(dimensions: SIMD2<Int32>)
  -> MTLTexture? {
  var texture: MTLTexture?
  let skyTexture = MDLSkyCubeTexture(
    name: "sky",
    channelEncoding: .float16,
    textureDimensions: dimensions,
```

<a id="page-531"></a>

```
    turbidity: skySettings.turbidity,
    sunElevation: skySettings.sunElevation,
    upperAtmosphereScattering:
      skySettings.upperAtmosphereScattering,
    groundAlbedo: skySettings.groundAlbedo)
  do {
    let textureLoader =
      MTKTextureLoader(device: Renderer.device)
    texture = try textureLoader.newTexture(
      texture: skyTexture,
      options: nil)
  } catch {
    print(error.localizedDescription)
  }
  return texture
}
```

Model I/O uses your settings to create the sky texture. That’s all there is to creating a procedurally generated sky texture!

➤ Call the new method at the end of init(textureName:):

```
if let textureName {
  // load named texture here
} else {
  skyTexture = loadGeneratedSkyboxTexture(dimensions: [256,
256])
}
```

You’ll add the if part of this conditional shortly and load the named texture. The nil option provides a default sky.

To render the texture, you’ll change the skybox shader function and ensure that the texture gets to the GPU.

➤ Still in Skybox.swift, in render(encoder:uniforms:), add the following code before the draw call:

```
encoder.setFragmentTexture(
  skyTexture,
  index: SkyboxTexture.index)
```

The starter project already has the necessary texture enumeration indices set up in Common.h for the skybox textures.

➤ Open Skybox.metal, and add a new property to VertexOut:

`float3 textureCoordinates;`

<a id="page-532"></a>

Generally, when you load a model, you also load its texture coordinates. However, when sampling texels from a cube texture, instead of using a uv coordinate, you use a 3D vector. For example, a vector from the center of any unit cube passes through the far top left corner at [-1, 1, 1].

![Figure](Metal_by_Tutorials_v500mpdf/72336c4978283c06f8817885.png)

_Skybox coordinates_

Conveniently, even though the skybox’s far top-left vertex position is [-0.5, 0.5, 0.5], it still lies on the same vector, so you can use the skybox vertex position for the texture coordinates.

➤ Add this code to vertex\_skybox before return out;:

`out.textureCoordinates = in.position.xyz;`

➤ Change `fragment_skybox` to:

```
fragment half4 fragment_skybox(
  VertexOut in [[stage_in]],
  texturecube<half> cubeTexture [[texture(SkyboxTexture)]])
{
  constexpr sampler default_sampler(filter::linear);
  half4 color = cubeTexture.sample(
    default_sampler,
    in.textureCoordinates);
  return color;
}
```

<a id="page-533"></a>

Accessing a cube texture is similar to accessing a 2D texture. You mark the cube texture as texturecube in the shader function parameters and sample it using the textureCoordinates vector that you set up in the vertex function.

➤ Build and run the app, and you now have a realistic sky, simulating physics:

![Figure](Metal_by_Tutorials_v500mpdf/eb6551908c0ed9e638932395.png)

_A procedural sky_

## **Custom Sky Textures**

As mentioned earlier, you can use your own 360º sky textures. The textures included in the starter project were downloaded from Poly Haven (https://polyhaven.com/ hdris) — a great place to find environment maps. Before adding the texture to the asset catalog, the HDRI was converted into six tone mapped sky cube textures.

Note: If you want to create your own skybox textures from an HDR file, you can use the HDR2Cube app included with this chapter’s resources. This app creates six PNG images from which you can create a cube texture in the asset catalog.

Loading a cube texture is almost the same as loading a 2D texture.

<a id="page-534"></a>

➤ Open TextureController.swift, and examine loadCubeTexture(imageName:). You can load either a cube texture from the asset catalog or one 2D image consisting of the six faces vertically.

➤ Open Skybox.swift, and at the end of init(textureName:), in the first half of the incomplete conditional, replace // load named texture here with this:

```
skyTexture = TextureController.loadCubeTexture(
  imageName: textureName)
```

You load the texture using the given texture name.

➤ Open **GameScene.swift**, and in `init()`, change the skybox initialization to:

`skybox = Skybox(textureName: "sky")`

➤ Build and run the app to see your new skybox texture.

![Figure](Metal_by_Tutorials_v500mpdf/54d12af0786009e5ecf465c3.png)

_The skybox_

Notice that as you zoom and rotate the scene, although the skybox rotates with the rest of the scene, it does not reposition.

You should be careful that the sky textures you use don’t have objects that appear to be close, as they will always appear to stay at the same distance from the camera. Sky textures should be for background only. This skybox texture is not a great fit as the background does not match the ground plane.

<a id="page-535"></a>

## Reﬂection

Now that you have something to reflect, you can easily implement reflection of the sky onto the car. When rendering the car, all you have to do is take the camera view direction, reflect it about the surface normal, and sample the skycube along the reflected vector for the fragment color for the car.

![Figure](Metal_by_Tutorials_v500mpdf/ff465c87d604283377a0e81b.png)

_Reflection_

Included in the starter project is a new fragment shader that you’ll work on to implement alternative PBR lighting using the skybox as the lighting source instead of SceneLighting.

➤ In the Shaders folder, open IBL.metal. fragment\_IBL loads up all the textures that you’re already familiar with in fragment\_main. Instead of calculating the diffuse and specular, the function returns the base color.

➤ Open **Pipelines.swift**, and change `"fragment_main"` in `createForwardPSO()` to:

`"fragment_IBL"`

<a id="page-536"></a>

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/9266c876d6e2bcd2824bbf3b.png)

_Color textures only_

The fragment shader renders the car and ground returning the texture base color. The glass windshield has transparency, so uses a different pipeline. It will render transparently with specular highlights, as it did before.

➤ Open Skybox.swift, and add this to Skybox:

```
func update(encoder: MTLRenderCommandEncoder) {
  encoder.setFragmentTexture(
    skyTexture,
    index: SkyboxTexture.index)
}
```

You send the skybox texture to the fragment shader. You’ll add other skybox textures to this method soon.

➤ Open ForwardRenderPass.swift, and in draw(commandBuffer:scene:uniforms:params:), add the following code before var params = params:

`scene.skybox?.update(encoder: renderEncoder)`

The sky texture is now available to the GPU.

<a id="page-537"></a>

➤ Open IBL.metal, and add the skybox texture to the parameter list for fragment\_IBL:

`texturecube<float> skybox [[texture(SkyboxTexture)]]`

You read the skybox texture using the type texturecube. Instead of providing 2D uv coordinates, you’ll provide 3D coordinates.

You now calculate the camera’s reflection vector about the surface normal to get a vector for sampling the skybox texture. To get the camera’s view vector, you subtract the fragment world position from the camera position.

➤ At the end of `fragment_IBL`, before `return color;`, add this:

```
float3 viewDirection =
  in.worldPosition.xyz - params.cameraPosition;
viewDirection = normalize(viewDirection);
float3 textureCoordinates =
  reflect(viewDirection, normal);
```

Here, you calculate the view vector and reflect it about the surface normal to get the vector for the cube texture coordinates.

➤ Now, add this:

```
constexpr sampler defaultSampler(filter::linear);
color = skybox.sample(
  defaultSampler, textureCoordinates);
float4 copper = float4(0.722, 0.451, 0.2, 1);
color = color * copper;
```

Here, you sample the skybox texture for a color and multiply it by a copper color.

<a id="page-538"></a>

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/62b445cd624a9ac23f9ef40d.png)

_Reflections_

The rendered scene now appears to be made of beautifully shiny copper. As you rotate the scene, using your mouse or trackpad, you can see the sky reflected in the scene models.

Note: This is not a true reflection since you’re only reflecting the sky texture. If you place any objects in the scene, they won’t be reflected. However, this reflection is a fast and easy effect, and is often sufficient.

➤ In fragment\_IBL, remove the code you just added, i.e., the lines from constexpr sampler defaultSampler... to color = color \* copper;.

You’ll replace this deleted code with new lighting code shortly.

<a id="page-539"></a>

## **Image-Based Lighting**

At the beginning of the chapter, there were two problems with the original car render. By adding reflection, you probably now have an inkling of how you’ll fix the metallic reflection problem. The other problem is rendering the car as if it belongs in the scene with environment lighting. IBL or Image-Based Lighting is one way of dealing with this problem.

Using the sky image you can extract lighting information. For example, the parts of the car that face the sun in the sky texture should shine more than the parts that face away. The parts that face away shouldn’t be entirely dark but should have ambient light filled in from the sky texture.

Epic Games developed a technique for Fortnite, which they adapted from Disney’s research. This technique has become the standard for IBL in games today. If you want to be as physically correct as possible, there’s a link to their article on how to achieve this included with the references.markdown for this chapter.

You’ll be doing an approximation of their technique, making use of Model I/O for the diffuse.

## Diffuse Reﬂection

Light comes from all around us. Sunlight bounces around and colors reflect. When rendering an object, you should take into account the color of the light coming from every direction.

![Figure](Metal_by_Tutorials_v500mpdf/2ad9f847a7a2e9fbe0ed5215.png)

_Diffuse reflection_

Using every direction is somewhat of an impossible task, but you can use convolution to compute a cube map called an irradiance map from which you can extract lighting information. You won’t need to know the mathematics behind this: Model I/O comes to the rescue again!

The diffuse reflection for the car will come from a second texture derived from the sky texture.

<a id="page-540"></a>

➤ Open Skybox.swift, and add a new property to Skybox to hold this diffuse texture:

`var diffuseTexture: MTLTexture?`

➤ To create the diffuse irradiance texture, add this temporary method:

```
mutating func loadIrradianceMap() {
  // 1
  guard let skyCube =
    MDLTexture(cubeWithImagesNamed: ["cube-sky.png"])
  else { return }
  // 2
  let irradiance =
    MDLTexture.irradianceTextureCube(
      with: skyCube,
      name: nil,
      dimensions: [64, 64],
      roughness: 0.6)
  // 3
  let loader = MTKTextureLoader(device: Renderer.device)
  do {
    diffuseTexture = try loader.newTexture(
    texture: irradiance,
    options: nil)
  } catch {
    fatalError(error.localizedDescription)
  }
}
```

Going through this code:

1. Model I/O currently doesn’t load cube textures from the asset catalog, so, in the Textures folder, your project has an image named cube-sky.png with the six faces included in it. Each of the faces is 128 x 128 pixels.

2. Use Model I/O to create the irradiance texture from the source image. Neither source nor destination textures have to be large, as the diffuse color is spread out.

3. Load the resultant MDLTexture to diffuseTexture.

➤ In Skybox.swift, add the following code to the end of init(textureName:):

`loadIrradianceMap()`

➤ In `update(encoder:)`, add the following:

`encoder.setFragmentTexture(`

<a id="page-541"></a>

diffuseTexture,   index: SkyboxDiffuseTexture.index)

This code will send the diffuse texture to the GPU.

➤ Open IBL.metal, and add the diffuse texture to the parameter list for fragment\_IBL:

```
texturecube<float> skyboxDiffuse
[[texture(SkyboxDiffuseTexture)]]
```

➤ At the end of fragment\_IBL, add this before return color;:

```
float4 diffuse = skyboxDiffuse.sample(textureSampler, normal);
color = diffuse * float4(material.baseColor, 1);
```

The diffuse value doesn’t depend on the angle of view, so you sample the diffuse texture using the surface normal. You then multiply the result by the base color.

➤ Build and run the app. Because of the irradiance convolution, the app may take a minute or so to start. As you rotate about the car, you’ll notice it’s very slightly brighter where it faces the skybox sun.

![Figure](Metal_by_Tutorials_v500mpdf/65e12a3973df886d6324b5c8.png)

_Diffuse from irradiance_

<a id="page-542"></a>

➤ Click the Capture GPU frame icon to enter the GPU Debugger, and look at the generated irradiance map.

![Figure](Metal_by_Tutorials_v500mpdf/3f7acd615e567193fe298814.png)

➤ Double-click the texture to see the generated texture.

![Figure](Metal_by_Tutorials_v500mpdf/d462bb9e9cfbeed16a5c5d37.png)

Instead of generating the irradiance texture each time, you can save the irradiance map to a file and load it from there. Included in the resources folder for this chapter is a project named IrradianceGenerator. You can use this app to generate your irradiance maps.

<a id="page-543"></a>

In your project, in the Textures folder, there’s a touched-up irradiance map named irradiance.png that matches and brightens the sky texture. It’s time to switch to using this irradiance map for the diffuse texture instead of generating it.

➤ Open Skybox.swift, and in init(textureName:), locate where you load skyTexture from a given name in the if closure, and add the following code immediately after loading skyTexture:

```
diffuseTexture =
  TextureController.loadCubeTexture(
    imageName: "irradiance.png")
```

➤ Remove the method loadIrradianceMap(), and also remove the call to loadIrradianceMap() at the end of init(textureName).

➤ Build and run the app to see results using the brighter prebuilt irradiance map.

![Figure](Metal_by_Tutorials_v500mpdf/ec4ee6f974587b5e7fa33eb5.png)

_Brighter irradiance_

<a id="page-544"></a>

## Specular Reﬂection

The irradiance map provides the diffuse and ambient reflection, but the specular reflection is a bit more difficult.

You may remember from Chapter 10, “Lighting Fundamentals”, that, whereas the diffuse reflection comes from all light directions, specular reflection depends upon the angle of view and the roughness of the material.

![Figure](Metal_by_Tutorials_v500mpdf/dee00b5ab471b666ebd2dbf3.png)

_Specular reflection_

In Chapter 11, “Maps &amp; Materials”, you had a foretaste of physically based rendering using the Cook-Torrance microfacet specular shading model. This model is defined as:

![Figure](Metal_by_Tutorials_v500mpdf/747b18d7895395121bb66552.png)

<a id="page-545"></a>

Where you provide the light direction (l), view direction (v) and the half vector (h) between l and v. As described, the functions are:

• D: Geometric micro-facet slope distribution

• F: Fresnel

• G: Geometric attenuation

Just as with the diffuse light, to get the accuracy of the incoming specular light, you need to take many samples, which is impractical in real-time rendering. Epic Games’s approach in their paper, Real Shading in Unreal Engine 4 (http:// blog.selfshadow.com/publications/s2013-shading-course/karis/ s2013\_pbs\_epic\_notes\_v2.pdf), is to split up the shading model calculation. They prefilter the sky cube texture with the geometry distribution for various roughness values. For each roughness level, the texture gets smaller and blurrier, and you can store these pre-filtered environment maps as different mipmap levels in the sky cube texture.

Note: In the resources for this chapter, there’s a project named Specular, which uses the code from Epic Games’s paper. This project takes in six images — one for each cube face — and will generate pre-filtered environment maps for as many levels as you specify in the code. The results are placed in a subdirectory of Documents named specular, which you should create before running the project. You can then add the created .png files to the mipmap levels of the sky cube texture in your asset catalog.

➤ In **Textures.xcassets**, look at the **sky** texture.

**sky** already contains the pre-filtered environment maps for each mip level.

![Figure](Metal_by_Tutorials_v500mpdf/b9f9fe0100f87afba420d907.png)

_Pre-filtered environment maps_

<a id="page-546"></a>

## **BRDF Look-Up Table**

To calculate the final color, you use a Bidirectional Reflectance Distribution Function (BRDF) that takes in the actual roughness of the model and the current viewing angle and returns the scale and bias for the Fresnel and geometric attenuation contributions.

You can encapsulate this BRDF in a look-up table (LUT) as a texture that behaves as a two-dimensional array. One axis is the roughness value of the object, and the other is the angle between the normal and the view direction. You input these two values as the UV coordinates and receive back a color. The red value contains the scale, and the green value contains the bias.

![Figure](Metal_by_Tutorials_v500mpdf/871d5ad15f00d92b20e0e1ad.png)

_A BRDF LUT_

The more photorealistic you want your scene to be, the higher the level of mathematics you’ll need to know. In the resources folder for this chapter, in references.markdown, you’ll find links with suggested reading that explain the Cook-Torrance microfacet specular shading model.

In the Utility/BRDF folder, your project contains functions provided by Epic Games to create the BRDF look-up texture. You’ll now implement the compute shader that builds the BRDF look-up texture.

➤ Open **Skybox.swift**, and add a property for the new texture:

`var brdfLut: MTLTexture?`

➤ At the end of init(textureName:), call the method supplied in the starter project to build the texture:

`brdfLut = Renderer.buildBRDF()`

<a id="page-547"></a>

Renderer.buildBRDF() uses a complex compute shader in BRDF.metal to create a new texture.

➤ Still in Skybox.swift, in update(encoder:), add the following code to send the texture to the GPU:

```
encoder.setFragmentTexture(
  brdfLut,
  index: BRDFLutTexture.index)
```

➤ Build and run the app, and click the **Capture GPU frame** icon to verify the lookup texture created by the BRDF compute shader is available to the GPU.

![Figure](Metal_by_Tutorials_v500mpdf/21e7173cc2b718d8b1b7ae5c.png)

_BRDF LUT is on the GPU_

Notice the texture format is RG16Float. As a float format, this pixel format has a greater accuracy than RGBA8Unorm.

All the necessary information is now on the GPU, so you need to receive the new BRDF look-up texture into the fragment shader and do the shader math.

➤ Open IBL.metal, and add the new parameter to fragment\_IBL:

`texture2d<float> brdfLut [[texture(BRDFLutTexture)]]`

➤ At the end of `fragment_IBL`, replace `return color;` with this:

<a id="page-548"></a>

```
// 1
constexpr sampler s(filter::linear, mip_filter::linear);
float3 prefilteredColor
  = skybox.sample(
    s,
    textureCoordinates,
    level(material.roughness * 10)).rgb;
// 2
float nDotV = saturate(dot(normal, -viewDirection));
float2 envBRDF
  = brdfLut.sample(s, float2(material.roughness, nDotV)).rg;
return float4(envBRDF, 0, 1);
```

Going through the code:

1. Read the skybox texture along the reflected vector as you did earlier. Using the extra parameter level(n), you can specify the mip level to read. You sample the appropriate mipmap for the roughness of the fragment.

2. Calculate the angle between the view direction and the surface normal, and use this as one of the UV coordinates to read the BRDF look-up texture. The other coordinate is the roughness of the surface. You receive back the red and green values which you’ll use to calculate the second part of the Cook Torrence equation.

➤ Build and run the app to see the result of the BRDF look-up.

![Figure](Metal_by_Tutorials_v500mpdf/fd0bc554ffe553d65e28e43a.png)

_The BRDF look up result_

At glancing angles on the car, the result is green.

<a id="page-549"></a>

## Fresnel Reﬂectance

When light hits an object straight on, some of the light is reflected. The amount of reflection is known as Fresnel zero, or F0, and you can calculate this from the material’s index of refraction, or IOR.

When you view an object, at the viewing angle of 90º, the surface becomes nearly 100% reflective. For example, when you look across the water, it’s reflective; but when you look straight down into the water, it’s non-reflective.

![Figure](Metal_by_Tutorials_v500mpdf/4a6626b12254714ec821df6c.png)

Most dielectric (non-metal) materials have an F0 of about 4%, so most rendering engines use this amount as standard. For metals, F0 is the base color.

➤ Replace `return float4(envBRDF, 0, 1);` with:

```
float3 f0 = mix(0.04, material.baseColor.rgb,
material.metallic);
float3 specularIBL = f0 * envBRDF.r + envBRDF.g;
```

Here, you choose F0 as 0.04 for non-metals and the base color for metals. metallic should be a binary value of 0 or 1, but it’s best practice to avoid conditional branching in shaders, so you use mix(). You then calculate the second part of the rendering equation using the values from the look-up table.

➤ Add the following code after the code you just added:

```
float3 specular = prefilteredColor * specularIBL;
color += float4(specular, 1);
return color;
```

<a id="page-550"></a>

color now includes the diffuse from the irradiance skybox texture, the material base color and the specular value.

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/73e91df2c37b46bdf3e54193.png)

_Diffuse and specular_

Your car render is almost complete. Non-metals take the roughness value — the seats are matte, and the car paint is shiny. Metals reflect but take on the base color — the base color of the wheel hubs and the steel bar behind the seats is gray.

## **Tweaking**

Being able to tweak shaders gives you complete power over how your renders look. Because you’re using low dynamic range lighting, the non-metal diffuse color looks a bit dark. You can tweak the color very easily.

➤ In fragment\_IBL, after float4 diffuse = skyboxDiffuse.sample(textureSampler, normal);, add this:

```
diffuse = mix(pow(diffuse, 0.2), diffuse, material.metallic);
diffuse *= calculateShadow(in.shadowPosition, shadowTexture);
```

This code raises the power of the diffuse value but only for non-metals. You also reinstate the shadow.

<a id="page-551"></a>

➤ Build and run, and notice the scene is a lot brighter.

![Figure](Metal_by_Tutorials_v500mpdf/7257d0bcb51747968b150e4a.png)

_Tweaking the shader_

The finishing touch will be to add a fake shadow effect using ambient occlusion. At the rear of the car, the exhaust pipes look as if they are self-lit:

![Figure](Metal_by_Tutorials_v500mpdf/e356cb24651544019786b450.png)

They should be shadowed because they are recessed. This is where ambient occlusion maps come in handy.

## **Ambient Occlusion Maps**

Ambient occlusion is a technique that approximates how much light should fall on a surface. If you look around you — even in a bright room — where surfaces are very close to each other, they’re darker than exposed surfaces. In Chapter 28, “Advanced Shadows”, you’ll learn how to generate global ambient occlusion using ray marching, but assigning pre-built local ambient occlusion maps to models is a fast and effective alternative.

<a id="page-552"></a>

Apps such as Adobe Substance Painter can examine the model for proximate surfaces and produce an ambient occlusion map. This is the AO map for the car:

![Figure](Metal_by_Tutorials_v500mpdf/481d841c6e3a121556ba5519.png)

The white areas on the left, with a color value of 1.0, are UV mapped to the car paint. These are fully exposed areas. When you multiply the final render color by 1.0, it’ll be unaffected. However, you can identify the wheel at the bottom right of the AO map, where the spokes are recessed. Those areas have a color value of perhaps 0.8, which darkens the final render color.

The ambient occlusion map is included in racing-car.usdz and all set up in the starter project, ready to use.

➤ Open **IBL.metal**, and in `fragment_IBL`, just before the final `return`, add this:

`color *= material.ambientOcclusion;`

➤ Build and run the app, and compare the exhaust pipes to the previous render.

![Figure](Metal_by_Tutorials_v500mpdf/9680a15076f901496db5cf74.png)

All of the recessed areas are darker, which gives more natural lighting to the model.

<a id="page-553"></a>

## **Challenge**

On the first page of this chapter is a comparison of the car rendered in two different lighting situations. Your challenge is to create the red lighting scene.

Provided in the resources folder for this chapter, are six cube face png images converted from an HDRI downloaded from Poly Haven (https://polyhaven.com).

1. Create an irradiance map using the included IrradianceGenerator project in resources/Sky Projects, and import the generated map into the project.

2. Create specular mipmap levels using the included Specular project.

3. Create a new cube texture in the asset catalog. In the Attributes inspector, change the Mipmap Levels of each of the six faces to Fixed with nine levels.

4. Assign this new cube texture the appropriate generated mipmap images. The base level should be the original png files from the resources folder. In the Attributes inspector, ensure that the textures have an origin of Bottom Left and the interpretation is Colors.

5. In SceneLighting.swift, change the sun light’s position to [-1, 0.5, 2] to match the skybox.

Aside from the light position in SceneLighting, and the name of the sky texture in GameScene, there’s no code to change — it’s all imagery! You’ll find the completed project in the challenge directory for this chapter.

![Figure](Metal_by_Tutorials_v500mpdf/a9f934b7245e1710de287bc2.png)

_Completed challenge_

<a id="page-554"></a>

## **Key Points**

• Using a cuboid skybox, you can surround your scene with a texture.

• Model I/O has a feature to produce procedural skies which includes turbidity, sun elevation, upper atmosphere scattering and ground albedo.

• Cube textures have six faces. Each of the faces can have mipmaps.

• Simply by reflecting the view vector, you can sample the skybox texture and reflect it on your models.

• Image-based lighting uses the sky texture for lighting. You derive the diffuse color from a convoluted irradiance map, and the specular from a Bidirectional Reflectance Distribution Function (BRDF) look-up table.

## **Where to Go From Here?**

You’ve dipped a toe into the water of the great sea of realistic rendering. If you want to explore more about this fascinating topic, references.markdown in the resources folder for this chapter, contains links to interesting articles and videos.

This chapter did not touch on spherical harmonics, which is an alternative method to using an irradiance texture map for diffuse reflection. Mathematically, you can approximate that irradiance map with 27 floats. Hopefully, the links in references.markdown will get you interested in this amazing technique.

Before you try to achieve the ultimate realistic render, one question you should ask yourself is whether your game will actually benefit from realism. One way to stand out from the crowd is to create your own rendering style. Games such as Fortnite aren’t entirely realistic and have a style all of their own. Experiment with shaders to see what you can create.

<a id="page-555"></a>

# 22

# Chapter 22: Reﬂection &amp; Refraction

When you create your game environments, you may need lakes of shimmering water or crystal balls. To look realistic, shiny glass objects require both reflection and refraction.

Reflection is one of the most common interactions between light and objects. Imagine looking into a mirror. Not only would you see your image being reflected, but you’d also see the reflection of any nearby objects.

Refraction is another common interaction between light and objects that you often see in nature. While it’s true that most objects in nature are opaque — thus absorbing most of the light they get — the few objects that are translucent, or transparent, allow for the light to propagate through them.

![Figure](Metal_by_Tutorials_v500mpdf/2b9a82de2e889ea74727e7ec.png)

_Reflection and refraction_

<a id="page-556"></a>

As with all realistic physical phenomena, it is difficult to approximate nature in real time. We’re rapidly approaching higher GPU efficiency where ray tracing algorithms may be viable in games, but for a quick and easy solution, rasterized reflection and refraction is the way to go.

An exemplary algorithm for creating realistic water was developed by Michael Horsch in 2005 (https://is.gd/h9azi2). This realistic water algorithm is purely based on lighting and its optical properties, as opposed to having a water simulation based on physics.

## **The Starter Project**

➤ In Xcode, open the starter project for this chapter.

The starter project is similar to the project at the end of the previous chapter, with a few additions that include:

• GameScene.swift contains a new scene with new models and renders a new skybox texture. You can move around the scene using WASD keys, and look about using the mouse or trackpad. Scrolling the mouse wheel, or pinching on iOS, moves you up and down, so you can get better views of your lake. The number 1 key will position the camera looking down on the scene, and number 2 will return the camera to its original position.

• WaterRenderPass.swift, in the Render Passes folder, contains a new render pass. It’s similar to  ForwardRenderPass, but refactors the command encoder setup into a new render method. WaterRenderPass is all set up and ready to render in Renderer, but it will do nothing until you assign it a render pass descriptor.

• Water.swift, in the Geometry folder, contains a new Water class, similar to Model. The class loads a primitive mesh plane and is set up to render the plane with its own pipeline state.

• Pipelines.swift has new pipeline state creation methods to render water and a terrain.

<a id="page-557"></a>

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/7b8fc126a948d9165f3601f8.png)

_The starter app_

Visitors to this quaint cottage would love a recreational lake for swimming and fishing.

## **Terrains**

Many game scenes will have a ground terrain, or landscape, and this terrain may need its own shader. The starter project includes Terrain.swift, which contains Terrain, a subclass of Model. Changing shaders entails loading a new pipeline state, so Terrain creates its own pipeline state object along with a texture for use later.

Terrain.metal holds the fragment function to render the terrain. After you’ve added some water, you’ll change the terrain texture to blend with an underwater texture.

Instead of including the ground when rendering the scene models, ForwardRenderPass renders the terrain separately, as you did for the skybox.

## **Rendering Rippling Water**

Now that you’re acquainted with the code, here’s the plan on how you’ll proceed through the chapter:

1. Render a large horizontal quad that will be the surface of the water.

2. Render the scene to a reflection texture.

3. Use a clipping plane to limit what geometry you render.

<a id="page-558"></a>

4. Distort the reflection using a normal map to create ripples on the surface.

5. Render the scene to a refraction texture.

6. Apply the Fresnel effect so that the dominance of each texture will change depending on the viewing angle.

7. Add smoothness to the water depth visibility using a depth texture.

Ready? It’s going to be a wild ride but stick around until the end, because you won’t want to miss this.

## **1. Creating the Water Surface**

➤ In the **Geometry** folder, open **Water.swift**, and examine the code.

Similar to Model, Water initializes a mesh and is Transformable, so you can position, rotate and scale the mesh. The mesh is a plane primitive. Water also has a render method where you’ll add textures and render the mesh plane.

➤ Open Pipelines.swift, and locate createWaterPSO(vertexDescriptor:).

The water pipeline will need new shader functions. You’ll name the vertex function vertex\_water and the fragment function fragment\_water.

## **Creating the Water Shaders**

➤ In the **Shaders** folder, create a new Metal file named **Water.metal**, and add this:

```
#import "Common.h"

struct VertexIn {
  float4 position [[attribute(Position)]];
  float2 uv [[attribute(UV)]];
};

struct VertexOut {
  float4 position [[position]];
  float4 worldPosition;
  float2 uv;
};

vertex VertexOut vertex_water(
  const VertexIn in [[stage_in]],
  constant Uniforms &uniforms [[buffer(UniformsBuffer)]])
{
```

<a id="page-559"></a>

```
  float4x4 mvp = uniforms.projectionMatrix * uniforms.viewMatrix
                   * uniforms.modelMatrix;
  VertexOut out {
    .position = mvp * in.position,
    .uv = in.uv,
    .worldPosition = uniforms.modelMatrix * in.position
  };
  return out;
}

fragment float4 fragment_water(
  VertexOut in [[stage_in]],
  constant Params &params [[buffer(ParamsBuffer)]])
{
  return float4(0.0, 0.05, 0.2, 1.0);
}
```

This code provides a minimal configuration for rendering the water surface quad. The vertex function moves the mesh into position, and the fragment function shades the mesh a bluish color.

## **Adding the Water to Your Scene**

➤ Open **GameScene.swift**, and add a new property:

`var water: Water?`

➤ Add the following code to init():

```
water = Water()
water?.position = [0, -1, 0]
```

With this code, you initialize and position the water plane.

➤ Open ForwardRenderPass.swift, and in draw(commandBuffer:scene:uniforms:params:), locate where you render the skybox.

➤ Add the following code immediately before rendering the skybox:

```
scene.water?.render(
  encoder: renderEncoder,
  uniforms: uniforms,
  params: params)
```

<a id="page-560"></a>

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/1711bc2d6a4b28d7b92586c2.png)

_The initial water plane_

The cottage is now a waterfront vacation home.

## 2. Rendering the Reﬂection

The water plane should reflect its surroundings. In Chapter 21, “Image-Based Lighting”, you reflected the skybox onto objects, but this time you’re also going to reflect the house and terrain on the water.

You’re going to render the scene to a texture from a point underneath the water pointing upwards. You’ll then take this texture and render it flipped on the water surface.

![Figure](Metal_by_Tutorials_v500mpdf/28b9738680479d8ed8dbd980.png)

You’ll do all this in WaterRenderPass.

➤ Open WaterRenderPass.swift.

<a id="page-561"></a>

WaterRenderPass initializes the pipeline and depth stencil states. Each frame, Renderer calls waterRenderPass.draw(commandBuffer:scene:uniforms:params:), which renders the entire scene (minus the water). Currently the render pass doesn’t render anything, because descriptor is nil and the app exits the method.

➤ In WaterRenderPass, add this to init():

`descriptor = MTLRenderPassDescriptor()`

You initialize a new render pass descriptor.

➤ Add some new texture properties to WaterRenderPass:

```
var reflectionTexture: MTLTexture?
var refractionTexture: MTLTexture?
var depthTexture: MTLTexture?
```

You’ll keep both a reflection and a refraction texture, as you’ll render these textures from different camera positions. Although you’re setting up the refraction texture, you won’t be using it until later in the chapter.

➤ In `resize(view:size:)`, add this:

```
let size = CGSize(
  width: size.width / 2, height: size.height / 2)
reflectionTexture = Self.makeTexture(
  size: size,
  pixelFormat: view.colorPixelFormat,
  label: "Reflection Texture")
refractionTexture = Self.makeTexture(
  size: size,
  pixelFormat: view.colorPixelFormat,
  label: "Refraction Texture")
depthTexture = Self.makeTexture(
  size: size,
  pixelFormat: .depth32Float,
  label: "Reflection Depth Texture")
```

Any time you can save on memory, you should. For reflection and refraction you don’t really need sharp images, so you create the textures at half the usual size.

<a id="page-562"></a>

➤ Add the following code to the top of draw(commandBuffer:scene:uniforms:params:):

```
let attachment = descriptor?.colorAttachments[0]
attachment?.texture = reflectionTexture
attachment?.storeAction = .store
let depthAttachment = descriptor?.depthAttachment
depthAttachment?.texture = depthTexture
depthAttachment?.storeAction = .store
```

You’ll render color to the reflectionTexture, depth to depthTexture and ensure that the GPU stores the textures for later use. Because you’ll render the skybox — which will cover the whole render target — you don’t care what the load actions are.

The water plane will use these render textures, so you’ll store them to Water.

➤ In the Geometry folder, open Water.swift, and add the new properties to Water:

```
weak var reflectionTexture: MTLTexture?
weak var refractionTexture: MTLTexture?
weak var refractionDepthTexture: MTLTexture?
```

➤ In render(encoder:uniforms:params:), add the following code before the draw call:

```
encoder.setFragmentTexture(
  reflectionTexture,
  index: 0)
encoder.setFragmentTexture(
  refractionTexture,
  index: 1)
```

Soon, you’ll change the `fragment_water` shader to use these textures.

➤ Open WaterRenderPass.swift, and add the following code to the top of draw(commandBuffer:scene:uniforms:params:):

```
guard let water = scene.water else { return }
water.reflectionTexture = reflectionTexture
water.refractionTexture = refractionTexture
water.refractionDepthTexture = depthTexture
```

Here, you pass on the render target textures to `Water` for texturing the water plane.

➤ Build and run the app to see progress so far.

<a id="page-563"></a>

You won’t see any obvious changes, but capture the GPU workload and check out the water render pass:

![Figure](Metal_by_Tutorials_v500mpdf/0dbeec357d3352ab3d401014.png)

WaterRenderPass renders an exact duplicate of the scene, not including the water plane, to the reflection render target texture.

➤ In the Shaders folder, open Water.metal, and add new parameters to fragment\_water:

```
texture2d<float> reflectionTexture [[texture(0)]],
texture2d<float> refractionTexture [[texture(1)]]
```

You’re concentrating on reflection for now, but you’ll use the refraction texture later.

➤ In `fragment_water`, replace the return line with this:

```
// 1
constexpr sampler s(filter::linear, address::repeat);
// 2
float width = float(reflectionTexture.get_width() * 2.0);
float height = float(reflectionTexture.get_height() * 2.0);
float x = in.position.x / width;
float y = in.position.y / height;
float2 reflectionCoords = float2(x, 1 - y);
// 3
float4 color = reflectionTexture.sample(s, reflectionCoords);
color = mix(color, float4(0.0, 0.05, 0.2, 1.0), 0.3);
return color;
```

<a id="page-564"></a>

Going through the code:

1. Create a new sampler with linear filtering and repeat addressing mode, so that the texture tiles at the edge if necessary.

2. Determine the reflection coordinates which will use an inverted y value because the reflected image is a mirror of the scene above the water surface. Notice you multiply by 2.0. You do this because the texture is only half-size.

3. Sample the color from the reflection texture, and mix it a little with the previous bluish color the water plane had before.

➤ Build and run the app, and you’ll see the house, terrain and sky reflected on the water surface.

![Figure](Metal_by_Tutorials_v500mpdf/c3b96ccd5a4b128f2501471d.png)

_Initial reflection_

It looks nice now, but rotate the camera with your mouse or trackpad, or press the number 1 key to view from above, and you’ll see the reflection is incorrect. You need to render the reflection target from a different camera position.

![Figure](Metal_by_Tutorials_v500mpdf/6581fcac887b39d540c327aa.png)

_Incorrect reflection_

<a id="page-565"></a>

➤ Open WaterRenderPass.swift, and in draw(commandBuffer:scene:uniforms:params:), add the following code before calling render(renderEncoder:scene:uniforms:params:).

```
var reflectionCamera = scene.camera
reflectionCamera.rotation.x *= -1
let position = (scene.camera.position.y - water.position.y) * 2
reflectionCamera.position.y -= position

var uniforms = uniforms
uniforms.viewMatrix = reflectionCamera.viewMatrix
```

Here, you use a separate camera specially for reflection, and position it below the surface of the water to capture what’s above the surface.

➤ Build and run the app to see the updated result:

![Figure](Metal_by_Tutorials_v500mpdf/839154a210cd9a5c59d94a56.png)

_Reflected camera position_

That didn’t work out too well. You’d expect to see the sky reflected in the water.

As the main camera moves up the y-axis, the reflection camera moves down the y-axis to below the terrain surface which blocks the view to the sky. You could temporarily solve this by culling the terrain’s back faces when you render, but this may introduce other rendering artifacts. A better way of dealing with this issue is to clip the geometry you don’t want to render.

<a id="page-566"></a>

## **3. Creating Clipping Planes**

A clipping plane, as its name suggests, clips the scene using a plane. It’s hardware accelerated, meaning that if geometry is not within the clip range, the GPU immediately discards the vertex and doesn’t put it through the entire pipeline. You may get a significant performance boost as some of the geometry will not need to get processed by the fragment shaders anymore.

For the reflection texture, you only need to render the scene as if from under the water, flip it, and add it to the final render.

Placing the clipping plane at the level of the water, ensures that only the scene geometry above the water is rendered to the reflection texture.

![Figure](Metal_by_Tutorials_v500mpdf/3f8495531843c9478a9dfb95.png)

_The clipping plane_

➤ Still in WaterRenderPass.swift, in draw(commandBuffer:scene:uniforms:params:), after the previous code, add this:

```
var clipPlane = float4(0, 1, 0, -water.position.y)
uniforms.clipPlane = clipPlane
```

With this code, you create clipPlane as a var because you’ll adjust it shortly for refraction.

The clipping plane xyz is a direction vector that denotes the clipping direction. The last component is the level of the water.

<a id="page-567"></a>

➤ In the Shaders folder, open Common.h, and add a new member to Uniforms:

`vector_float4 clipPlane;`

➤ Open ShaderDefs.h, and add a new member to VertexOut:

`float clip_distance [[clip_distance]] [1];`

Notice the Metal Shading Language attribute, clip\_distance, which is one of the built-in attributes exclusively used by vertex shaders. The clip\_distance attribute is an array of distances, and the [1] argument represents its size — a 1 in this case because you only need one member in the array.

Even though the vertex function returns VertexOut, the fragment shader functions are using FragmentIn in place of VertexOut. FragmentIn was a duplicate of VertexOut, because [[clip\_distance]] is a vertex-only attribute, and fragment functions now wouldn’t compile if they used VertexOut.

Note: You can read more about matching vertex and fragment attributes in the Metal Shading Language specification (https://developer.apple.com/metal/ Metal-Shading-Language-Specification.pdf), in Section 5.7.1 “Vertex- Fragment Signature Matching.”

➤ Open Vertex.metal, and add this to vertex\_main before return:

```
out.clip_distance[0] =
  dot(uniforms.modelMatrix * in.position, uniforms.clipPlane);
```

Any negative result in vertex\_out.clip\_distance[0] will result in the vertex being clipped.

You’re now clipping any geometry processed by vertex\_main. You could also clip the skybox in the same way, but when you later add ripples, they may go below the clipping plane, leaving nothing to reflect.

<a id="page-568"></a>

➤ Build and run the app, capture the GPU workload and examine the output of the Water Render Pass.

![Figure](Metal_by_Tutorials_v500mpdf/08da2a07e165ddf1b239954f.png)

_Rendering above the clipping plane_

All rendered scene model geometry is clipped, but the skybox still renders.

➤ Continue running the app, move the camera up and rotate it to look downwards.

![Figure](Metal_by_Tutorials_v500mpdf/644ff6597809aa188a9e5b15.png)

_Reflecting the sky correctly_

The sky now reflects correctly and your water reflection appears smooth and calm. As you move the camera up and down, the reflection is now consistent.

Still water, no matter how calming, isn’t realistic. Time to give that water some ripples.

<a id="page-569"></a>

## **4. Rippling Normal Maps**

➤ Open Textures.xcassets, and select normal-water. This is a normal map that you’ll use for the water ripples.

![Figure](Metal_by_Tutorials_v500mpdf/a2e1f3e892f70c3f88dae46e.png)

_The water ripple normal map_

You’ll tile this map across the water and move it, perturbing the water normals, which will make the water appear to ripple.

➤ In the Geometry folder, open Water.swift, and add these new properties to Water:

```
var waterMovementTexture: MTLTexture?
var timer: Float = 0
```

You add the texture, and a timer so that you can animate the normals.

➤ Add the following code to the end of init():

```
waterMovementTexture =
  TextureController.loadTexture(name: "normal-water")
```

➤ In render(encoder:uniforms:params:), add the following code where you set the other fragment textures:

```
encoder.setFragmentTexture(
  waterMovementTexture,
  index: 2)
var timer = timer
encoder.setFragmentBytes(
  &timer,
  length: MemoryLayout<Float>.size,
  index: 3)
```

<a id="page-570"></a>

Here, you send the texture and the timer to the fragment shader.

➤ Add this new method to Water:

```
func update(deltaTime: Float) {
  let sensitivity: Float = 0.005
  timer += deltaTime * sensitivity
}
```

`deltaTime` will be too fast, so you include a sensitivity modifier.

➤ Open GameScene.swift, and add this to the top of update(deltaTime:):

`water?.update(deltaTime: deltaTime)`

`GameScene` will update the water timer every frame.

You’ve now set up the texture and the timer on the CPU side.

➤ Open Water.metal, and add two new parameters for the texture and timer to fragment\_water:

```
texture2d<float> normalTexture [[texture(2)]],
constant float& timer [[buffer(3)]]
```

➤ Add the following code before you define color:

```
// 1
float2 uv = in.uv * 2.0;
// 2
float waveStrength = 0.1;
float2 rippleX = float2(uv.x + timer, uv.y);
float2 rippleY = float2(-uv.x, uv.y) + timer;
float2 ripple =
  ((normalTexture.sample(s, rippleX).rg * 2.0 - 1.0) +
  (normalTexture.sample(s, rippleY).rg * 2.0 - 1.0))
  * waveStrength;
reflectionCoords += ripple;
// 3
reflectionCoords = clamp(reflectionCoords, 0.001, 0.999);
```

Going through the code:

1. Get the texture coordinates and multiply them by a tiling value. For 2 you get huge, ample ripples, while for 16 you get quite small ripples. Pick a value that suits your needs.

<a id="page-571"></a>

2. Calculate ripples by distorting the texture coordinates with the timer value. Only grab the R and G values from the sampled texture because they are the U and V coordinates that determine the horizontal plane where the ripples will be. The B value is not important here. waveStrength is an attenuator value, that gives you weaker or stronger waves.

3. Clamp the reflection coordinates to eliminate anomalies around the margins of the screen.

➤ Build and run the app, and you’ll see gorgeous ripples on the water surface.

![Figure](Metal_by_Tutorials_v500mpdf/021b2d81037ba02f39b38845.png)

_Calming water ripples_

## **5. Adding Refraction**

Implementing refraction is very similar to reflection, except that you only need to preserve the part of the scene below the clipping plane.

![Figure](Metal_by_Tutorials_v500mpdf/010da4747d5c1ac7cdb5c4c8.png)

_Rendering below the clipping plane_

➤ Open WaterRenderPass.swift, and add this to the end of draw(commandBuffer:scene:uniforms:params:):

```
// 1
descriptor.colorAttachments[0].texture = refractionTexture
// 2
guard let refractEncoder =
commandBuffer.makeRenderCommandEncoder(
  descriptor: descriptor) else {
```

<a id="page-572"></a>

```
  return
}
refractEncoder.label = "Refraction"
// 3
uniforms.viewMatrix = scene.camera.viewMatrix
clipPlane = float4(0, -1, 0, -water.position.y)
uniforms.clipPlane = clipPlane
// 4
render(
  renderEncoder: refractEncoder,
  scene: scene,
  uniforms: uniforms,
  params: params)
refractEncoder.endEncoding()
```

Going through the code:

1. Set the refraction texture as the render target.

2. Create a new render command encoder.

3. Set the y value of the clip plane to -1 since the camera is now in its original position and pointing down toward the water.

4. Render all the elements of the scene again.

➤ Build and run the app, capture the GPU workload and check out the refraction texture.

![Figure](Metal_by_Tutorials_v500mpdf/f03c911e03285b699da4b360.png)

_The refraction texture_

<a id="page-573"></a>

This time, the GPU has only rendered the scene geometry below the clipping plane.

You’re already sending the refraction texture to the GPU, so you can work on the calculations straightaway.

➤ Open Water.metal, and, in fragment\_water, add this below where you define reflectionCoords:

`float2 refractionCoords = float2(x, y);`

For refraction you don’t have to flip the `y` coordinate.

➤ Similarly, add this below reflectionCoords += ripple;:

`refractionCoords += ripple;`

➤ And once more, add this after the reflection line preventing edge anomalies:

`refractionCoords = clamp(refractionCoords, 0.001, 0.999);`

➤ Finally, replace:

`float4 color = reflectionTexture.sample(s, reflectionCoords);`

➤ With:

`float4 color = refractionTexture.sample(s, refractionCoords);`

You temporarily show only the refraction texture. You’ll return and include reflection shortly.

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/ded47cdb249994fba904e017.png)

_Refraction_

<a id="page-574"></a>

The reflection on the water surface is gone, and instead, you have refraction through the water.

There’s one more visual enhancement you can make to your water to make it more realistic: adding rocks and grime. Fortunately, the project already has a texture that can simulate this.

➤ Open Terrain.metal, and in fragment\_terrain, uncomment the section under // uncomment this for pebbles.

➤ Build and run the app, and you’ll now see a pebbled texture underwater.

![Figure](Metal_by_Tutorials_v500mpdf/d9bb0eeecda48de39502dbdf.png)

_Pebbles_

The holy grail of realistic water, however, is having a Fresnel effect that harmoniously combines reflection and refraction based on the viewing angle.

## **6. The Fresnel Effect**

The Fresnel effect is a concept you’ve seen in previous chapters. As you may remember, the viewing angle plays a significant role in the amount of reflection you can see. What’s new in this chapter is that the viewing angle also affects refraction but in inverse proportion:

• The steeper the viewing angle is, the weaker the reflection and the stronger the refraction.

• The shallower the viewing angle is, the stronger the reflection and the weaker the refraction.

<a id="page-575"></a>

The Fresnel effect in action:

![Figure](Metal_by_Tutorials_v500mpdf/4b4b717beaa805d0647c7da5.png)

➤ Open **Water.metal**, and in `fragment_water` before you define `color`, add this:

```
float3 viewVector =
  normalize(params.cameraPosition - in.worldPosition.xyz);
float mixRatio = dot(viewVector, float3(0, 1, 0));
return mixRatio;
```

Here, you work out the view vector between the camera and the water fragment. The mix ratio will be the blend between reflection and refraction.

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/f1368bc4b34fd373d9855656.png)

_The mix ratio between refraction and reflection_

As you move about the scene, the greater the angle between the camera and the water, the whiter the water becomes. A view across the water, down close to the water, returns black.

Instead of rendering black and white, you’ll mix between the refraction and reflection textures. Where the mix ratio is black, you’ll render the reflection texture, and where it’s white, refraction. A ratio of 0.5 would mean that reflection and refraction are mixed equally.

<a id="page-576"></a>

➤ Replace:

```
return mixRatio;
float4 color = refractionTexture.sample(s, refractionCoords);
```

➤ With:

```
float4 color =
  mix(reflectionTexture.sample(s, reflectionCoords),
      refractionTexture.sample(s, refractionCoords),
      mixRatio);
```

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/41b903be037478aff6898101.png)

_Refraction and Reflection_

Move the camera around and notice how reflection predominates for a small viewing angle while refraction predominates when the viewing angle is getting closer to 90 degrees (perpendicular to the water surface).

## 7. Adding Smoothness Using a Depth Texture

Light propagation varies for different transparent media. But for water, the colors with longer wavelengths (closer to infrared) quickly fade away as the light ray goes deeper. The bluish colors (closer to ultraviolet) tend to be visible at greater depths because they have shorter wavelengths.

<a id="page-577"></a>

At very shallow depths, however, most light should still be visible. You’ll make the water look smoother as depth gets smaller. You can improve the way the water surface blends with the terrain by using a depth map.

![Figure](Metal_by_Tutorials_v500mpdf/f6bd0310b82de9c9f09acb00.png)

_Water has hard edges_

➤ Open Water.swift, and add the following code to render(encoder:uniforms:params:) when you set the other fragment textures:

```
encoder.setFragmentTexture(
  refractionDepthTexture,
  index: 3)
```

In addition to sending the refraction texture from the refraction render pass, you’re now sending the depth texture too.

➤ Open Pipelines.swift, and add this to createWaterPSO(vertexDescriptor:) before the return:

```
let attachment = pipelineDescriptor.colorAttachments[0]
attachment?.isBlendingEnabled = true
attachment?.rgbBlendOperation = .add
attachment?.sourceRGBBlendFactor = .sourceAlpha
attachment?.destinationRGBBlendFactor = .oneMinusSourceAlpha
```

Here, you configure the blending options on the color attachment just as you did in Chapter 20, “Fragment Post-Processing.”

➤ Open Water.metal, and add the depth texture parameter to fragment\_water:

`depth2d<float> depthMap [[texture(3)]]`

➤ Add the following code before you set rippleX and rippleY:

```
float far = 100;    // the camera's far plane
float near = 0.1;   // the camera's near plane
```

<a id="page-578"></a>

```
float proj33 = far / (far - near);
float proj43 = proj33 * -near;
float depth = depthMap.sample(s, refractionCoords);
float floorDistance = proj43 / (depth - proj33);
depth = in.position.z;
float waterDistance = proj43 / (depth - proj33);
depth = floorDistance - waterDistance;
```

You convert the non-linear depth to a linear value.

Note:  Why and how you convert from non-linear to linear is mathematically complex. gamedev.net forums (https://is.gd/7Eha6g) has an explanation of converting a non-linear depth buffer value to a linear depth value.

Finally, add this before return:

`color.a = clamp(depth * 0.75, 0.0, 1.0);`

Here, you change the alpha channel so that blending goes into effect.

➤ Build and run the app, and you’ll now see a smoother blending of the shore with the terrain.

![Figure](Metal_by_Tutorials_v500mpdf/a1bfd082e4b365e1c1ccb47a.png)

_Blending at the water's edge_

<a id="page-579"></a>

## **Key Points**

• Reflection and refraction are important for realistic water and glass.

• Rasterizing reflections and refraction will not produce as good a result as ray tracing. But when speed is a concern, then ray tracing is not often viable.

• Because you’re using different view angles, you’ll need to create separate render passes to render the textures. For reflection, move the camera in the inverse direction from the plane to be reflected and flip the result.

• You already knew about near and far clipping planes, but you can also add your own custom clipping planes. A negative clip distance from in the vertex function will result in the GPU discarding the vertex.

• You can animate normal maps to provide water turbulence.

• The Fresnel effect depends upon viewing angle and affects reflection and refraction in inverse proportion.

## **Where to Go From Here?**

You’ve certainly made a splash with this chapter! If you want to explore more about water rendering, the references.markdown file in the resources folder for this chapter contains links to interesting articles and videos.

<a id="page-580"></a>

# 23

# Chapter 23: Animation

Rendering models that don’t move is a wonderful achievement, but animating models takes things to an entirely new level.

To animate means to bring to life. So what better way to play with animation than to render characters with personality and body movement. In this chapter, you’ll find out how to do basic animation using keyframes.

<a id="page-581"></a>

## **The Starter Project**

➤ In Xcode, open the starter project for this chapter, and build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/8f893948212f54e7697ac92f.png)

The scene is a simple one with just a ground plane and a ball. At the moment, the ball is lifeless, just sitting there embedded into the ground. To liven things up, you’ll start off by making it roll around the scene.

In the Animation folder, BallAnimations.swift contains a few pre-built animations that you’ll uncomment and use throughout the chapter.

## **Animation**

Animators like Winsor McCay and Walt Disney brought life to still images by filming a series of hand-drawn pictures one frame at a time.

![Figure](Metal_by_Tutorials_v500mpdf/ac00a455aef21186a51acdc2.png)

_Winsor McCay: Gertie the Dinosaur_

<a id="page-582"></a>

This frame-by-frame animation was — and still is — very time consuming. With the rise of computer animation, artists can now create 3D models and record their positions at specific points in time. From there, the computer interpolates, or tweens, the values between those positions, making the animation process a lot less time consuming. But there is another option: procedural animation.

## **Procedural Animation**

Procedural animation uses mathematics to calculate transformations over time. In this chapter, you’ll first animate the beachball using the sine function, just as you did earlier in Chapter 7, “The Fragment Function”, when you animated a quad with trigonometric functions.

To begin, you’ll create a structure that controls the ball’s animation.

➤ In the **Game** folder, add a new Swift file named **Beachball.swift**, and add this:

```
struct Beachball {
  var ball: Model
  var currentTime: Float = 0

  init(model: Model) {
    self.ball = model
    ball.position.y = 1
  }

  mutating func update(deltaTime: Float) {
    currentTime += deltaTime
  }
}
```

Here, you initialize Beachball with the model reference and create a method that GameScene will call every frame. (You’ll use the timer to animate your model over time.)

➤ Open **GameScene.swift**, and add a new property:

`lazy var beachball = Beachball(model: ball)`

➤ Then, add the following code to the top of update(deltaTime:):

`beachball.update(deltaTime: deltaTime)`

All of the ball’s movement and animation will now take place in Beachball.

<a id="page-583"></a>

➤ Open Beachball.swift, and add the following code to the end of update(deltaTime:):

`ball.position.x = sin(currentTime) * 2`

This code updates the ball’s x position every frame by double the sine of the accumulated current time.

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/37226395867fff86ded50d44.png)

_Side to side sine animation_

The ball now moves from side-to-side.

Sine is useful for procedural animation. By changing the amplitude, period and frequency, you can create waves of motion — although, for a ball, that’s not very realistic. However, with some physics, you can add a little bounce to its movement.

## **Animation Using Physics**

Instead of creating animation by hand using an animation app, you can use physics-based animation, which means that your models can simulate the real world. In this next exercise, you’re going to simulate only gravity and a collision. However, a full physics engine can simulate all sorts of effects, such as fluid dynamics, cloth and soft body (rag doll) dynamics.

➤ Create a new property in `Beachball` to track the ball’s velocity:

`var ballVelocity: Float = 0`

➤ Remove the following code from update(deltaTime:):

`ball.position.x = sin(currentTime) * 2`

<a id="page-584"></a>

➤ In update(deltaTime:), set some constants for the individual physics that you’ll need for the simulation:

```
let gravity: Float = 9.8 // meter / sec2
let mass: Float = 0.05
let acceleration = gravity / mass
let airFriction: Float = 0.2
let bounciness: Float = 0.9
let timeStep: Float = 1 / 600
```

gravity represents the acceleration of an object falling to Earth. If you’re simulating gravity elsewhere in the universe, for example, Mars, this value would be different. Newton’s Second Law of Motion is F = ma or force = mass \* acceleration. Rearranging the equation gives acceleration = force (gravity) / mass. The other constants describe the surroundings and properties of the ball. If this were a bowling ball, it would have a higher mass and less bounce.

➤ Add this to the end of update(deltaTime:):

```
ballVelocity += (acceleration * timeStep) / airFriction
ball.position.y -= ballVelocity * timeStep

// collision with ground
if ball.position.y <= 0.35 {
  ball.position.y = 0.35
  ballVelocity = ballVelocity * -1 * bounciness
}
```

Here, you calculate the position of the ball based on the its current velocity. The ball’s origin is at its center, and it’s approximately 0.7 units in diameter. So when the ball’s center is 0.35 units above the ground, that’s when you reverse the velocity and travel upward.

➤ In `init(model:)`, change the ball’s initial position to be higher up in the air:

`ball.position.y = 3`

<a id="page-585"></a>

➤ Build and run the app, and watch the ball bounce.

![Figure](Metal_by_Tutorials_v500mpdf/d3c0d5cd18a74ca804677126.png)

_A bouncing ball_

This is a simple physics animation, but it demonstrates what you can do with very little code.

## **Axis-Aligned Bounding Box**

You hard-coded the ball’s radius so that it collides with the ground, but collision systems generally require some kind of bounding box to test whether an object collides with another object.

![Figure](Metal_by_Tutorials_v500mpdf/85392a9632ff14e005b68b77.png)

_Axis aligned bounding box_

A ball would benefit from a spherical bounding volume. Because your ball is simply using the y-axis, you can determine the ball’s height using an axis-aligned bounding box that Model I/O calculates.

<a id="page-586"></a>

➤ In the Geometry folder, open Model.swift. Then, add a bounding box property and a computed size property to Model:

```
var boundingBox = MDLAxisAlignedBoundingBox()
var size: float3 {
  return boundingBox.maxBounds - boundingBox.minBounds
}
```

➤ Next, add the following code to the end of init(name:):

`boundingBox = asset.boundingBox`

This code extracts the bounding box information from Model I/O.

➤ Open Beachball.swift, and in update(deltaTime:), update the collision code with the correct size calculated from the bounding box value:

```
// collision with ground
if ball.position.y <= ball.size.y / 2 {
  ball.position.y = ball.size.y / 2
  ballVelocity = ballVelocity * -1 * bounciness
}
```

➤ Build and run the app, and your ball will collide with the ground, precisely at the edge of the ball.

![Figure](Metal_by_Tutorials_v500mpdf/2ac496f31752b7f89f32a9fc.png)

_Collision with the ground_

<a id="page-587"></a>

## **Keyframes**

Let’s animate the ball getting tossed around by adding some input information about its position over time. For this input, you’ll need an array of positions so that you can extract the correct position for the specified time.

In the Animation folder, in BallAnimations.swift, there’s an array already set up: ballPositionXArray. This array contains sixty values ranging from -1 to 1, then back to -1. By calculating the current frame, you can grab the correct x position from the array.

➤ Open **Beachball.swift**, and replace `update(deltaTime:)` with:

```
mutating func update(deltaTime: Float) {
  currentTime += deltaTime
  ball.position.y = 1

  let fps: Float = 60
  let currentFrame =
    Int(currentTime * fps) % (ballPositionXArray.count)
  ball.position.x = ballPositionXArray[currentFrame]
}
```

Here, you calculate the current frame (based on 60 fps) and extract the correct value from the array.

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/438381229fdab72226353f96.png)

_Frame by frame animation_

<a id="page-588"></a>

Watch as the ball moves around in a mechanical, backward and forward motion over 60 frames. This is almost the same result as the sine animation, but instead, it’s animated using an array of values that you can control and re-use.

Here, you’re setting the position 60 times per second — but even at that speed, the animation appears jerky. If you were to lower the speed to 30 fps, the animation would look awful.

## **Interpolation**

It’s a lot of work inputting a value for each frame. If you’re just moving an object in a straight line from point A to B, you can interpolate the value. Interpolation is where you calculate a value given a range of values and a current location within the range. When animating, the current location is the current time as a percentage of the animation duration.

➤ To work out the time percentage, use the following formula:

![Figure](Metal_by_Tutorials_v500mpdf/6d4c32addf419c1c8abbcf19.png)

This formula results in a time value between 0 and 1.

For example, with a start value of 5, an end value of 10 and a duration of 2 seconds, after 1 second passes, the interpolated value is 7.5.

![Figure](Metal_by_Tutorials_v500mpdf/3ca39b1b247aaa9deeccc898.png)

That’s a linear interpolation, but you can use other formulas for interpolating.

![Figure](Metal_by_Tutorials_v500mpdf/64f543300df1c8540c098f54.png)

In the above image, linear interpolation is on the left. The x-axis is time, and the y-axis is value. You sample the value at the appropriate time. You can improve the ball’s animation using ease in / ease out interpolation (shown on the right) to make the animation less mechanical. With ease in / ease out, the ball gains speed slowly at the start and then slows down toward the end of the animation.

<a id="page-589"></a>

Instead of creating one value for every frame to animate your ball, you’ll hold only key positions. These positions will be the extreme of a pose. In the ball example, the extreme pose positions are -1 and 1. You’ll also hold key times that match the time of that key value. For example, if your animation is 2 seconds long, your extremes would be at 0 seconds for the starting pose on the left, 1 second for the ball to be on the right, and 2 seconds to take the ball back to the left again. All of the frames in between these times are interpolated.

➤ In the Animation folder, create a new Swift file named Animation.swift.

In this file, you’ll store your animation data and create methods to return the interpolated value at a given time.

➤ Add the following:

```
struct Keyframe<Value> {
  var time: Float = 0
  var value: Value
}
```

This code creates a structure to hold the animation key values and times. The value can be one of various types, so you make it generic.

➤ Now, add this:

```
struct Animation {
  var translations: [Keyframe<float3>] = []
  var repeatAnimation = true
}
```

This structure holds an array of keyframes where each translation will be a float3 value. repeatAnimation indicates whether to repeat the animation clip forever or play it just once.

➤ Add the following new method to Animation:

```
func getTranslation(at time: Float) -> float3? {
  // 1
  guard let lastKeyframe = translations.last else {
    return nil
  }
  // 2
  var currentTime = time
  if let first = translations.first,
    first.time >= currentTime {
    return first.value
  }
  // 3
```

<a id="page-590"></a>

```
  if currentTime >= lastKeyframe.time,
    !repeatAnimation {
    return lastKeyframe.value
  }
}
```

This method returns the interpolated keyframe.

Here’s the breakdown:

1. Ensure that there are translation keys in the array, otherwise, return a nil value.

2. If the first keyframe occurs on or after the time given, then return the first key value. The first frame of an animation clip should be at keyframe 0 to give a starting pose.

3. If the time given is greater than the last key time in the array, then check whether you should repeat the animation. If not, then return the last value.

➤ Add the following code to the bottom of getTranslation(at:):

```
// 1
currentTime = fmod(currentTime, lastKeyframe.time)
// 2
let keyFramePairs = translations.indices.dropFirst().map {
  (previous: translations[$0 - 1], next: translations[$0])
}
// 3
guard let (previousKey, nextKey) = (keyFramePairs.first {
  currentTime < $0.next.time
})
else { return nil }
// 4
let interpolant =
  (currentTime - previousKey.time) /
  (nextKey.time - previousKey.time)
// 5
return simd_mix(
  previousKey.value,
  nextKey.value,
  float3(repeating: interpolant))
```

<a id="page-591"></a>

Going through the code:

1. Use the modulo operation to get the current time within the clip.

2. Create a new array of tuples containing the previous and next keys for all keyframes, except the first one.

3. Find the first tuple of previous and next keyframes where the current time is less than the next keyframe time. The current time will, therefore, be between the previous and next keyframe times.

4. Use the interpolation formula to get a value between 0 and 1 for the progress percentage between the previous and next keyframe times.

5. Use simd\_mix to interpolate between the two keyframes. (interpolant must be a value between 0 and 1.)

➤ Open BallAnimations.swift, and uncomment ballTranslations.

ballTranslations is an array of seven Keyframes. The length of the clip is two seconds. You can see this by looking at the key time of the last keyframe.

In the x-axis, the ball will start off at position -1 and then move to position 1 at 0.35 seconds. It will hold its position until 1 second has passed, then return to -1 at 1.35 seconds. It will then hold its position until the end of the clip. By changing the values in the array, you can speed up the throw and hold the ball for longer at either end.

➤ Open **Beachball.swift**, and replace `update(deltaTime:)` with:

```
mutating func update(deltaTime: Float) {
  currentTime += deltaTime
  var animation = Animation()
  animation.translations = ballTranslations
  ball.position =
    animation.getTranslation(at: currentTime) ?? [0, 0, 0]
  ball.position.y += ball.size.y
}
```

<a id="page-592"></a>

Here, you load the animation clip with the generated keyframe translations. Generally, you’ll want to load the animation clip outside of the update, but for the sake of simplicity, in this example, handling things within update(deltaTime:) is fine.

You then extract the ball’s position from the animation clip for the current time.

➤ Build and run the app, and watch as creepy invisible hands toss your ball around.

![Figure](Metal_by_Tutorials_v500mpdf/95d95509bfc5e0bcdf9d427a.png)

_Tossing the ball_

Note: Notice the trajectory of the ball on the y-axis. It currently goes up and down in diagonal straight lines. Better keyframing can fix this.

## **Euler Angle Rotations**

Now that you have the ball translating through the air, you probably want to rotate it as well. To express rotation of an object, you currently hold a float3 with rotation angles on x, y and z axes. These are known as Euler angles after the mathematician Leonhard Euler. Euler is the man behind Euler’s rotation theorem — a theorem which states that any rotation can be described using three rotation angles. This is OK for a single rotation, but interpolating between these three values doesn’t work in a way that you may think.

➤ To create a rotation matrix, you’ve been calling this function, hidden in the math library in Utility/MathLibrary.swift:

```
init(rotation angle: float3) {
  let rotationX = float4x4(rotationX: angle.x)
  let rotationY = float4x4(rotationY: angle.y)
  let rotationZ = float4x4(rotationZ: angle.z)
  self = rotationX * rotationY * rotationZ
}
```

<a id="page-593"></a>

Here, the final rotation matrix is made up of three rotation matrices multiplied in a particular order. This order is not set in stone and is one of six possible orders. Depending on the multiplication order, you’ll get a different rotation.

Note: Sometimes, these rotations are referred to as Yaw-Pitch-Roll. You’ll see these names a lot in flight simulators, Depending on your frame of reference, if you’re using the y-axis as up and down (remember that’s not universal), then Yawing is about the y-axis, Pitching is about the x-axis and Rolling is about the z-axis.

For static objects within one rendering engine, this is fine. The main problem comes with animation and interpolating these angles.

As you proceed through a rotation interpolation if two axes become aligned you get the terrifyingly named gimbal lock.

![Figure](Metal_by_Tutorials_v500mpdf/4a777ef7dea2df608cb09905.png)

Gimbal lock means that you’ve lost one axis of rotation. Because the inner axis rotations build on the outer axis rotation, the two rotations overlap and cause odd interpolation.

## **Quaternions**

Multiplying x, y and z rotations without compelling a sequence on them is impossible unless you involve the fourth dimension. In 1843, Sir William Rowan Hamilton did just that: he inscribed his fundamental formula for quaternion multiplication on to a stone on a bridge in Dublin.

![Figure](Metal_by_Tutorials_v500mpdf/8a04b7bf7009c821702a619e.png)

The formula uses four-dimensional vectors and complex numbers to describe rotations. The mathematics is complicated, but fortunately, you don’t have to understand how quaternions work to use them.

<a id="page-594"></a>

The main benefit of quaternions are:

• They interpolate correctly when using spherical linear interpolation (or slerp).

• They never lose any axes of control.

• They always take the shortest path between two rotations unless you specifically ask for the longest path.

Note: If you’re interested in studying the internals of quaternions, references.markdown contains further reading.

You don’t have to write any complicated interpolation code because simd has quaternion classes and methods that handle everything for you. simd\_slerp() performs a spherical interpolation along the shortest path as shown in the following image.

![Figure](Metal_by_Tutorials_v500mpdf/7fd71f85f895ce1b5bdb749e.png)

_Spherical interpolation_

Internally in simd, quaternions are vectors of four elements, but Apple suggests that you treat them as abstract mathematical objects rather than delving into internal storage. That lets you off the hook for learning that the last element of the quaternion is the real part, and the first three elements are the imaginary part.

You’ll switch from using Euler rotations to using quaternions for your rotations. Taking advantage of simd conversion of quaternions to and from rotation matrices, this switch is almost effortless.

<a id="page-595"></a>

➤ In the Geometry folder, open Transform.swift, add a new property to Transform and change the definition of rotation:

```
var quaternion = simd_quatf(.identity)
var rotation: float3 = [0, 0, 0] {
  didSet {
    let rotationMatrix = float4x4(rotation: rotation)
    quaternion = simd_quatf(rotationMatrix)
  }
}
```

You initialize the quaternion to a zero rotation and keep the quaternion value in sync when you set a model’s rotation.

➤ In the extension where you define modelMatrix, change the definition of rotation to:

`let rotation = float4x4(quaternion)`

➤ In the `Transformable` extension, add this:

```
var quaternion: simd_quatf {
  get { transform.quaternion }
  set { transform.quaternion = newValue }
}
```

With this syntactic sugar, when you refer to the model.transform.quaternion, you can now instead shorten it to model.quaternion.

To animate using quaternion rotation, you’ll duplicate what you did for translations.

➤ Open Animation.swift, and add a new property to Animation:

`var rotations: [Keyframe<simd_quatf>] = []`

This time the keyframes will be quaternion values.

➤ Duplicate getTranslation(at:) to a new method called getRotation(at:), that uses rotations and quaternions instead of translations and floats:

```
func getRotation(at time: Float) -> simd_quatf? {
  guard let lastKeyframe = rotations.last else {
    return nil
  }
  var currentTime = time
  if let first = rotations.first,
    first.time >= currentTime {
    return first.value
```

<a id="page-596"></a>

```
  }
  if currentTime >= lastKeyframe.time,
    !repeatAnimation {
    return lastKeyframe.value
  }
  currentTime = fmod(currentTime, lastKeyframe.time)
  let keyFramePairs = rotations.indices.dropFirst().map {
    (previous: rotations[$0 - 1], next: rotations[$0])
  }
  guard let (previousKey, nextKey) = (keyFramePairs.first {
    currentTime < $0.next.time
  })
  else { return nil }
  let interpolant =
    (currentTime - previousKey.time) /
    (nextKey.time - previousKey.time)
  return simd_slerp(
    previousKey.value,
    nextKey.value,
    interpolant)
}
```

Note that you change the interpolation function to use simd\_slerp instead of simd\_mix. This does the necessary spherical interpolation.

➤ Open BallAnimations.swift, and uncomment ballRotations.

ballRotations is an array of rotation keyframes. The rotation starts out at 0, then rotates by 90º on the z-axis over several keyframes to a rotation of 0 at 0.35 seconds. The reason for rotating several times by 90º is because if you rotate from 0º to 360º, the shortest distance between those is 0º, so the ball won’t rotate at all.

➤ Open **Beachball.swift**, and replace `update(deltaTime:)` with this:

```
mutating func update(deltaTime: Float) {
  currentTime += deltaTime
  var animation = Animation()
  animation.translations = ballTranslations
  animation.rotations = ballRotations
  ball.position =
    animation.getTranslation(at: currentTime)
      ?? float3(repeating: 0)
  ball.position.y += ball.size.y / 2
  ball.quaternion =
    animation.getRotation(at: currentTime)
      ?? simd_quatf()
}
```

<a id="page-597"></a>

You load the animation clip with both translation and rotation values. You then extract the values for position and quaternion for the given time.

➤ Build and run the app, and your ball moves back and forth with rotation.

![Figure](Metal_by_Tutorials_v500mpdf/d3cbb1e080bc0610e3125984.png)

_The ball rotates as it moves_

If you need more complex animations, you’ll probably want to create the animation in a 3D app like Blender and store it in a USD file.

## **USD and USDZ Files**

You briefly learned about some 3D file formats in Chapter 2, “3D Models”. Throughout this book, models are in the USD file format with the .usdz file extension, Apple’s preferred 3D format. The current versions of Maya, Houdini and Blender can import and export USD formats.

These are the various file extensions for the USD format:

• .usd: A Universal Scene Description (USD) file consists of assets or links to assets which allows multiple artists to work on the same scene. The file can hold massive scenes with mesh geometry, textures, animation and lighting information.

• .usdz: A single archive file that contains all the files - not just links - necessary for rendering a model.

• .usda: This file is the USD file in human readable text format.

• .usdc: This file is the USD file in binary format.

Sketchfab (http://sketchfab.com) is a major provider and showcase of 3D models. All their downloadable models are available converted to the USDZ format.

<a id="page-598"></a>

## **Animating Meshes**

In the Assets folder, the beachball.usdz file holds translation and rotation animation, and Model I/O can extract this animation in various ways.

Model I/O transform components don’t allow you to access the rotation and translation values directly. Instead, they provide you with a method that returns a transform matrix at a particular time. So for mesh transform animation, you’ll extract the animation data for every frame of the animation during the model loading process.

Note: When writing your own engine, you’ll have the choice to load this animation data up front for every frame, to match the transformation animation. You should consider the requirements of your game and what information your models hold. Generally it is more efficient to extract the loading code to a separate app which loads models and saves materials, textures and animation data into a more efficient format that matches your game engine. A good example of this asset pipeline is Apple’s video and sample code From Art to Engine with Model I/O from WWDC 2017 (https:// youtu.be/qxGhnC4\_PRc?si=tEvvZRutB9pyxP8w).

You’ll be running your game at a fixed fps - generally 60, and you’ll hold a transform matrix for every frame of animation.

➤ In the **Game** folder, open **GameController.swift**, and add a new property:

`static var fps: Double = 0`

You’ll use `fps` as the standard frames per second for your app.

➤ At the top of `init(metalView:options:)`, add this:

`Self.fps = Double(metalView.preferredFramesPerSecond)`

You set fps at the top of init(metalView:options:) because the models will use it when you initialize GameScene.

Model I/O can hold transform information on all objects within the MDLAsset. When you initialize Mesh, you’ll extract its transform animation, and then animate these transforms for the duration given by the asset.

<a id="page-599"></a>

➤ In the Animation folder, create a new file named TransformComponent.swift, and replace the default code with:

```
import ModelIO

struct TransformComponent {
  let keyTransforms: [float4x4]
  let duration: Float
  var currentTransform: float4x4 = .identity
  var objectMatrix: float4x4
}
```

You’ll hold all the transform matrices for each frame for the duration of the animation. For example, if the animation has a duration of 2.5 seconds at 60 frames per second, keyTransforms will have 150 elements. Later, you’ll update all of the Mesh’s currentTransform of every frame with the transform for the current frame taken from keyTransforms.

➤ Now, add the following to TransformComponent:

```
init(
  object: MDLObject,
  startTime: TimeInterval,
  endTime: TimeInterval
) {
  duration = Float(endTime - startTime)
  let timeStride = stride(
    from: startTime,
    to: endTime,
    by: 1 / TimeInterval(GameController.fps))
  keyTransforms = Array(timeStride).map { time in
    MDLTransform.globalTransform(
      with: object,
      atTime: time)
  }
  objectMatrix = object.transform?.matrix ?? .identity
  currentTransform = objectMatrix
}
```

This initializer creates all the transform matrices for every frame for the duration of the animation. If the object has an initial transform matrix, update the current transform with this matrix.

➤ Add the following to TransformComponent:

```
mutating func getCurrentTransform(at time: Float) {
  guard duration > 0 else {
    currentTransform = objectMatrix
    return
```

<a id="page-600"></a>

```
  }
  let frame = Int(fmod(time, duration) *
Float(GameController.fps))
  if frame < keyTransforms.count {
    currentTransform = keyTransforms[frame]
  } else {
    currentTransform = keyTransforms.last ?? .identity
  }
}
```

You retrieve a transform matrix at a given time. You calculate the current frame of the animation from the time. Using the floating point modulo operation fmod function, you can loop the animation. For example, if the animation is 2.5 seconds long, at 60 frames per second, that would mean there are 150 frames in the animation. If the current time is 5 seconds, that will be the last frame of the animation looped for a second time, and the current frame will be 150.

You save the current transform on the transform component. You’ll use the transform to update the position of the mesh vertices shortly.

The animation will need the start and end time from the asset.

➤ In the Geometry folder, open Mesh.swift, and add a new initializer to Mesh:

```
init(
  mdlMesh: MDLMesh,
  mtkMesh: MTKMesh,
  startTime: TimeInterval,
  endTime: TimeInterval
) {
  self.init(mdlMesh: mdlMesh, mtkMesh: mtkMesh)
}
```

➤ Open Model.swift, and in init(name:), locate Mesh(mdlMesh: $0.0, mtkMesh: $0.1) inside the meshes assignment.

➤ Change `Mesh(mdlMesh: $0.0, mtkMesh: $0.1)` to:

```
Mesh(
  mdlMesh: $0.0,
  mtkMesh: $0.1,
  startTime: asset.startTime,
  endTime: asset.endTime)
```

You use your new initializer in place of the old one.

<a id="page-601"></a>

➤ Back in Mesh.swift, add a new property to Mesh:

`var transform: TransformComponent?`

➤ Add the following code to the end of init(mdlMesh:mtkMesh:startTime:endTime:):

```
if mdlMesh.transform != nil {
  transform = TransformComponent(
    object: mdlMesh,
    startTime: startTime,
    endTime: endTime)
}
```

Now that you’ve set up the transform component with animation, you’ll be able to use it when rendering each frame.

➤ Open **Model.swift**, and add a new property to keep track of elapsed game time:

`var currentTime: Float = 0`

➤ Add a new method to Model:

```
func update(deltaTime: Float) {
  currentTime += deltaTime
  for index in 0..<meshes.count {
    meshes[index].transform?.getCurrentTransform(at:
currentTime)
  }
}
```

Here, you update all the transforms in the model ready for rendering.

➤ In the Renderer folder, open Rendering.swift, and in render(encoder:uniforms:params:), remove:

```
uniforms.modelMatrix = transform.modelMatrix
uniforms.normalMatrix = uniforms.modelMatrix.upperLeft

encoder.setVertexBytes(
  &uniforms,
  length: MemoryLayout<Uniforms>.stride,
  index: UniformsBuffer.index)
```

<a id="page-602"></a>

Some models may have multiple meshes, and you’ll have to change the model matrix for each mesh.

➤ At the top of the `for mesh in meshes` loop, add this:

```
let currentLocalTransform =
  mesh.transform?.currentTransform ?? .identity
uniforms.modelMatrix =
  transform.modelMatrix * currentLocalTransform
uniforms.normalMatrix = uniforms.modelMatrix.upperLeft
encoder.setVertexBytes(
  &uniforms,
  length: MemoryLayout<Uniforms>.stride,
  index: UniformsBuffer.index)
```

Here, you combine the model’s world transform with the mesh’s transform and send the uniforms to the vertex shader.

➤ Open GameScene.swift, and in update(deltaTime:), replace beachball.update(deltaTime:) with:

```
for model in models {
  model.update(deltaTime: deltaTime)
}
```

With this change, you’ll use the animation from the model file rather than from Beachball

➤ Build and run the app, and you’ll see an epic animation.

![Figure](Metal_by_Tutorials_v500mpdf/52222bd89c1ba703dffed771.png)

_The beachball USD animation_

Now that you’ve learned about simple mesh animation, you’re ready to move on to animating a jointed figure.

<a id="page-603"></a>

## **Key Points**

• Animation used to be done using frame-by-frame, but nowadays, animation is created on computers and is usually done using keyframes and interpolation.

• Procedural animation uses physics to compute values at a given time.

• Axis-aligned bounding boxes are useful when calculating collisions between aligned objects.

• Keyframes are generally extreme values between which the computer interpolates. This chapter demonstrates keyframing transformations, but you can animate anything. For example, you can set keyframes for color values over time.

• You can use any formula for interpolation, such as linear, or ease-in / ease-out.

• Interpolating quaternions is preferable to interpolating Euler angles.

• USD files are common throughout the 3D industry because you can keep the entire pipeline stored in the flexible format that USD provides.

<a id="page-604"></a>

# 24

# Chapter 24: Character Animation

In the previous chapter, you learned how to move objects over time using keyframes. Imagine how long it would take to create a walk cycle for a human figure by typing out keyframes. This is the reason why you generally use a 3D app, like Blender or Maya, to create your models and animations. You then export those animations to your game or rendering engine of choice.

<a id="page-605"></a>

## **Skeletal Animation**

When you animate a character, you rarely move its entire body. Even a walk cycle is animated in place, with the full body movement applied later. Instead, you’ll move parts of the mesh, such as an arm, rather than the whole thing. Using a 3D app, a rigger creates a skeleton — in Blender, this is known as an armature. The rigger assigns bones and other controls to parts of the mesh so that the animator can transform the bones and record the movement into an animation clip.

You’ll use Blender 4.5 to examine an animated model and understand the principles and concepts behind 3D animation.

Note: If you haven’t installed Blender 4.5 yet, it’s free, and you can download it from https://www.blender.org.

➤ Go to the resources folder for this chapter, and open skeleton.blend in Blender.

You’ll see something like this:

![Figure](Metal_by_Tutorials_v500mpdf/bd8afb5778de8d8a94b9bee1.png)

_The skeleton model in Blender 4.5_

Your Blender theme may have different colors.

<a id="page-606"></a>

➤ Before examining the bones further, left-click on the skeleton’s head to select the skeleton object. Press the Tab key to switch to Edit Mode:

![Figure](Metal_by_Tutorials_v500mpdf/2c81dd0ab712a14bf4c96807.png)

_The skeleton mesh_

Here, you can see all of the skeleton’s vertices as they were modeled. The skeleton has its arms stretched out in what’s known as the bind pose. Arms stretched out is a standard pose for figures as it makes it easier to add animation bones to the figure.

➤ Press the Tab key to go back to Object Mode.

Blender binds the vertices to the skeleton’s bones, with the arm down.

To animate the figure, you need to control groups of vertices. For example, to rotate the head, you’d rotate all of the head’s vertices.

Rigging a figure in Blender means creating an armature with a hierarchy of joints. Joints and bones are generally used synonymously, but a bone is simply a visual cue to see which joint affects which vertices.

The general process of creating a figure for animation goes like this:

1. Create the model.

2. Create an armature with a hierarchy of joints.

3. Apply the armature to the model with automatic weights.

4. Use weight painting to change which vertices go with each joint.

<a id="page-607"></a>

Just as in the song Dem Bones, “The toe bone’s connected to the foot bone,” this is how a typical rigged figure’s joint hierarchy might look:

![Figure](Metal_by_Tutorials_v500mpdf/3d47ec3be55b4ec3822ab3cc.png)

_A joint hierarchy_

In character animation, it’s (usually) all about rotation — your bones don’t translate unless you have some kind of disjointing skeleton. With this hierarchy of joints, when you rotate one joint, all the child joints follow. Try bending your elbow without moving your wrist. Because your wrist is lower in the hierarchy, even though you haven’t actively changed the wrist’s position and rotation, it still follows the movement of your elbow. This type of movement is known as forward kinematics and is what you’ll be using in this chapter. It’s a fancy name for making all child joints follow.

Note: Inverse kinematics allows the animator to make actions, such as walk cycles, more easily. Place your hand on a table or in a fixed position. Now, rotate your elbow and shoulder joint with your hand fixed. The hierarchical chain no longer moves your hand as in forward kinematics. As opposed to forward kinematics, the mathematics of inverse kinematics is quite complicated.

<a id="page-608"></a>

The skeleton model that you’re looking at in Blender has a limited rig for simplicity. It has four bones: the body, left upper arm, left forearm and left hand. Each of these joints controls a group of vertices.

## **Weight Painting in Blender**

➤ Left-click the skeleton’s head.

➤ At the bottom of the Blender window, click on the drop-down that currently reads Object Mode, and change it to Weight Paint.

![Figure](Metal_by_Tutorials_v500mpdf/f991402a25b485870fa4efe5.png)

_Weight Paint Dropdown_

The weight painting editor shows you how each bone affects the vertices. Currently the body vertex group is selected, which is attached to the body bone. All vertices affected by the body bone are shown in red. The arm mesh has its own bones and are shown here in blue.

![Figure](Metal_by_Tutorials_v500mpdf/cccc83f3abcde73f07b5b68c.png)

_The skeleton's body bone weights_

<a id="page-609"></a>

The process of weight painting and binding each bone to the vertices is called skinning. Unlike human arms, the skeleton’s arm bones here have space between them, so, in this case, the arm mesh is assigned to only one bone. However, if you’re rigging a human arm, you would typically weight the vertices to multiple bones.

Here’s a typically weighted arm with the forearm selected to show gradual blending of weights at the elbow and the wrist.

![Figure](Metal_by_Tutorials_v500mpdf/bea3c37f061add1da924f69f.png)

_A weighted arm_

This is a side-by-side example of blended and non-blended weights at the elbow joint with the forearm selected:

![Figure](Metal_by_Tutorials_v500mpdf/719cbe9aa4855e4f570807d3.png)

_Blended and non-blended weights_

The blue area indicates no weighting, whereas the red area indicates total weighting. You can see in the right image, the forearm vertices dig uncomfortably into the upper arm vertices, but in the left image, the vertices move more evenly around the elbow joint.

At the elbow, where the vertices are green, the vertex weighting would be 50% to the upper arm, and 50% to the forearm. When the forearm rotates, the green vertices will rotate at 50% of the forearm’s rotation. By blending the weights gradually, you can achieve an even deformation of vertices over the joint.

<a id="page-610"></a>

## **Animation in Blender**

➤ Select the drop-down at the bottom of the window that currently reads Weight Paint, and go back into Object Mode.

➤ Press the **space bar** to start an animation.

Your skeleton will now get friendly and wave at you. This wave animation is a 60 frame looping animation clip.

➤ At the top of Blender’s window, click the Animation tab to show the Animation workspace.

![Figure](Metal_by_Tutorials_v500mpdf/d7d02134f0c259bed4448f95.png)

You can now see the animation keys at the top left in the Dope Sheet. The dope sheet is a summary of the keyframes in the scene. It lists the joints on the left, and each circle in the dope sheet means there’s a keyframe at that frame.

![Figure](Metal_by_Tutorials_v500mpdf/1c26a0428a0139ec119acde5.png)

_The dope sheet_

Note: Although animated transformations are generally rotations, the keyframe can be a translation or a scale. You can click the arrow on the left of the joint name to see the specific channel the key is set on.

<a id="page-611"></a>

➤ Press space bar to stop the animation if it’s still going. Scrub through the animation by dragging the playhead at the top of the pane (the blue rectangle with 26 in it in the above image). Pause the playhead at each set of keyframes. Notice the position of the arm. At each keyframe, the arm is in an extreme position. Blender interpolates all the frames between the extremes.

Now that you’ve had a whirlwind tour of how to create a rigged figure and animate it in Blender, you’ll move on to learning how to render it in your rendering engine.

Note: You’ve only skimmed the surface of creating animated models. If you’re interested in creating your own, you’ll find some additional resources in references.markdown.

## **The Starter App**

➤ In Xcode, open the starter project and build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/224fd98e1fe83774c68ed0d0.png)

As well as the ground, you see a skeleton model called Skelly in .usdz format. The file contains an animation, but Skelly won’t wave until you’ve implemented the chapter code.

<a id="page-612"></a>

## **Implementing Skeletal Animation**

Importing a skeletal animation into your app is a bit more difficult than importing a simple USD file with transform animation because you have to deal with the joint hierarchy and joint weighting. You’ll read in the data from the USD file and restructure it to fit your rendering code.

This is how the objects will fit together in your app:

![Figure](Metal_by_Tutorials_v500mpdf/37064f2d7bb482cb3ed33e55.png)

_The code architecture_

Each model could have a number of animation clips, such as walk and wave. Each animation clip has a list of animations for a particular joint. Each animated model will have a Skeleton that establishes a joint hierarchy and holds a list of the joint names. Each Mesh will have a Skin that maps the mesh to the skeleton’s joints.

For each frame, you’ll use the animation data to calculate the position of each skinned mesh and work out the skeleton’s pose.

Note: It is possible for models to have more than one skeleton, but for simplicity, you’ll only hold one skeleton per model.

<a id="page-613"></a>

## **The Skeleton Map**

A Skeleton will hold the joint names in a String array. You’ll convert the skeleton’s hierarchy of joints to an array of parent indices.

In the following example, forearm.L is in position 2 in its array. Indexing at position 2 in the parent index array returns 1. The joint in position 1 is the forearm’s parent upperarm.L.

![Figure](Metal_by_Tutorials_v500mpdf/754467a98450a64243cc7616.png)

_The skeleton map_

## **Skin Data**

Each mesh will contain joint paths which bind the mesh to the skeleton. This is called skinning. On loading the mesh, you’ll load these joint paths in a Skin structure and map them to the skeleton’s joint paths.

![Figure](Metal_by_Tutorials_v500mpdf/50130cd7810c5a1117a1c673.png)

_Skin to skeleton map_

<a id="page-614"></a>

The Skelly model in your app is a single mesh which contains all joint paths. However, when you load Apple’s sample models at the end of the chapter, you may find forty meshes, each with different joint path mappings.

The starter project has a number of changes from the previous chapter, the most important being in the Animation folder:

• Animation.swift: Animation has methods to retrieve values at a given time. It now includes scale values in addition to the translations and rotations you added in the previous chapter.

• AnimationClip.swift: AnimationClip is a collection of Animations. You initialize AnimationClip with the animation held in the asset. You iterate through the joints and load up Animations for each joint. Model will hold a dictionary of AnimationClips keyed on the animation’s name.

• Skeleton.swift: Skeleton.init?(mdlSkeleton:) loads joint paths, parent indices, and bind transforms. You’ll calculate the current pose for each frame later.

• Skin.swift: Skin.init?(animationBindComponent:) loads joint paths and a skin to skeleton map. The initializer also initializes an MTLBuffer to hold the joint poses that you’ll calculate later in the chapter.

For simplicity in managing pipeline state objects, the project doesn’t implement shadows or transparency.

## **Initializing Data**

You’ll start by loading in the skeleton, the skinning data and lastly, the animations.

## **Loading the Skeleton**

➤ In the Geometry folder, open Model.swift, and add two new properties to Model:

```
var skeleton: Skeleton?
var animationClips: [String: AnimationClip] = [:]
```

If the asset is an animated character, you’ll store the skeleton and the animations.

<a id="page-615"></a>

➤ At the end of Model.swift, create a new extension with a method to load the skeleton:

```
// Animation
extension Model {
  func loadSkeleton(asset: MDLAsset) {
    let skeletons =
      asset.childObjects(of: MDLSkeleton.self) as? [MDLSkeleton]
?? []
    skeleton = Skeleton(mdlSkeleton: skeletons.first)
  }
}
```

You store the first skeleton in the asset.

## **Loading the Skinning Data**

Open Mesh.swift and add a new property to Mesh:

`var skin: Skin?`

For each mesh, you store optional skin to skeleton mapping data.

➤ Back in Model.swift, add a new method to Model, in the Animation extension, to load the skinned mesh:

```
func loadSkins(mdlMeshes: [MDLMesh]) {
  for index in 0..<mdlMeshes.count {
    let animationBindComponent =
      mdlMeshes[index].componentConforming(to:
MDLComponent.self)
        as? MDLAnimationBindComponent
      guard let skeleton else { continue }
      let skin = Skin(
        animationBindComponent: animationBindComponent,
        skeleton: skeleton)
      meshes[index].skin = skin
  }
}
```

You iterate through the Model I/O imported meshes. An MDLAnimationBindComponent holds the skinning data to map the mesh to the skeleton. You initialize Skin, which stores the relevant information and then you store the skin data on the mesh.

<a id="page-616"></a>

## **Loading the Animation**

➤ Add a new method to `Model` to load the animations from the asset:

```
func loadAnimations(asset: MDLAsset) {
  let assetAnimations = asset.animations.objects.compactMap {
    $0 as? MDLPackedJointAnimation
  }
  for assetAnimation in assetAnimations {
    let animationClip = AnimationClip(animation: assetAnimation)
    animationClips[assetAnimation.name] = animationClip
  }
}
```

Here, you extract all the MDLPackedJointAnimation objects from the asset and create AnimationClips. The animation clip will hold a dictionary of Animations for each joint path.

Each Animation will hold the translations and rotations along with the key times. Model.animationClips is a dictionary of animation clips keyed by animation name.

➤ At the end of `init(name:)`, call your new methods.

```
// load animated characters
loadSkeleton(asset: asset)
loadSkins(mdlMeshes: mdlMeshes)
loadAnimations(asset: asset)
```

Initialization is now complete.

➤ After the previous code, temporarily add this:

```
animationClips.forEach {
  print("Animations:", $0.key)
}
print(skeleton?.jointPaths)
```

➤ Build and run the app.

In the debug console, you’ll see a list of the available animations and a list of Skelly’s joints:

```
Animations: /skeleton/Animations/Wave
Optional(["/body", "/body/upperarm_L", "/body/upperarm_L/
forearm_L", "/body/upperarm_L/forearm_L/hand_L"])
nil
```

<a id="page-617"></a>

The joints correspond to the bones that that you previously saw in Blender. The nil at the end is from the ground model which isn’t animated and doesn’t have a skeleton.

➤ Remove the previous code that prints out the animations and skeleton.

## **The Math of Striking a Pose**

To update the skeleton’s pose every frame, you’ll create a method that takes the animation clip and iterates through the joints to update each joint’s position for the frame.

Each joint will have its own transforms which you’ll hold in an array called the joint matrix palette.

![Figure](Metal_by_Tutorials_v500mpdf/350eb2c85acd0791a72cd34a.png)

You’ll pass the matrix palette to the vertex shader to include with the other matrices that calculate the position of each vertex.

You’ll also pass extra vertex data to the shader, loaded from the model asset. Each vertex will have up to four joint indices which index into the matrix palette. The vertex data includes up to four weights which inform the shader of the influence of each joint.

This is how you’ll tackle the joint pose calculation:

1. Load the transforms from the animation clip for the current frame time. You’ll set up a local transform matrix for each joint in local joint space.

2. Traverse through the array of joints to combine the local transform matrix with its parent’s transform matrix.

3. The bind pose matrix holds the joint in world space. Taking the inverse of this completes the joint matrix palette calculations.

4. Update the joint matrix palette buffer for each skinned mesh.

You’ll then send the extra vertex data to the shader. In the shader, you’ll perform the matrix math using the matrix palette.

<a id="page-618"></a>

This is the pose for the first frame that you’ll finally achieve:

![Figure](Metal_by_Tutorials_v500mpdf/06f5ec7cb633419594dbaa30.png)

## **1. Load Animation Transform Data**

First set up a method to extract the current frame animation.

➤ In the Animation folder, open AnimationClip.swift, and add a new method to AnimationClip:

```
func getPose(at time: Float, jointPath: String) -> float4x4? {
  guard let jointAnimation = jointAnimation[jointPath],
    let jointAnimation = jointAnimation
    else { return nil }
  let rotation =
  jointAnimation.getRotation(at: time) ?? simd_quatf(.identity)
  let translation =
    jointAnimation.getTranslation(at: time) ?? float3(repeating:
0)
  let scale =
    jointAnimation.getScale(at: time) ?? float3(repeating: 1)
  let pose = float4x4(translation: translation) *
    float4x4(rotation) * float4x4(scaling: scale)
  return pose
}
```

<a id="page-619"></a>

Here, you retrieve the interpolated transformation, made up of rotation, translation and scale, for a given joint at a given time. You then create a transformation matrix for the joint and return it as the pose. This is much the same code as you used in the previous chapter for retrieving a transform at a particular time.

You’ll create the method that does all the math next.

➤ In the Animation folder, open Skeleton.swift, and add a new method to Skeleton:

```
func updatePose(
  at currentTime: Float,
  animationClip: AnimationClip
) {
  // 1
  let time = fmod(currentTime, animationClip.duration)
  // 2
  var localPose = [float4x4](
    repeating: .identity,
    count: jointPaths.count)
  // 3
  for index in 0..<jointPaths.count {
    let pose = animationClip.getPose(
      at: time * animationClip.speed,
      jointPath: jointPaths[index])
    ?? restTransforms[index]
    localPose[index] = pose
  }
}
```

Going through the code:

1. Calculate the animation’s current frame time by getting the floating point remainder of the current time divided by the animation duration. The animation will loop.

2. Initialize a matrix to hold all the skeleton’s joint transforms.

3. For each joint, retrieve the transform at the current time.

<a id="page-620"></a>

## **2. Calculate the World Pose**

In the following image, the forearm swings by 45º. All the other joint rotations are 0º. However, the rotation of the forearm affects the position (but not the rotation) of the hand.

![Figure](Metal_by_Tutorials_v500mpdf/d377582e9c843ef66efe8416.png)

You’ll iterate through the skeleton’s parent indices and multiply each parent’s local pose with its child’s local pose to transform the pose from joint space into its parent joint space.

➤ Continue by adding this to the end of updatePose(at:animationClip:):

```
var worldPose: [float4x4] = []
for index in 0..<parentIndices.count {
  let parentIndex = parentIndices[index]
  let localMatrix = localPose[index]
  if let parentIndex {
    worldPose.append(worldPose[parentIndex] * localMatrix)
  } else {
    worldPose.append(localMatrix)
  }
}
```

You iterate through the joint hierarchy to include the parent’s transforms on each joint.

![Figure](Metal_by_Tutorials_v500mpdf/6f75e3d010bfb22bb2a201fe.png)

_Array of transforms_

<a id="page-621"></a>

## **3. The Inverse Bind Matrix**

➤ Examine the properties held on Skeleton.

When you first instantiate the skeleton, you load these properties from the data loaded by Model I/O. One of the properties on Skeleton is  bindTransforms. This is an array of matrices, one element for each joint, that transforms vertices from their place in world space to the origin.

When all the joint transforms are set to identity, that’s when you’ll get the bind pose. If you apply the bind matrix to a joint, it will move to the origin. The following image shows the skeleton’s joints, in the bind pose, all multiplied by the bind transform matrix.

![Figure](Metal_by_Tutorials_v500mpdf/d5c44c083119cfba49bc4091.png)

_Bind matrix applied_

Why is this useful? Because rotation takes place around the origin.

<a id="page-622"></a>

To return the joint back to its original bind pose, you multiply each of the joint matrices by the inverse of the bind pose.

![Figure](Metal_by_Tutorials_v500mpdf/e37f7f834e50daef12070f8a.png)

_Inverse bind pose_

Note: Review Chapter 5, “3D Transformations” if you’re unsure of this rotation sequence.

➤ Add the following code to the end of updatePose(at:animationClip:):

```
for index in 0..<worldPose.count {
  worldPose[index] *= bindTransforms[index].inverse
}
currentPose = worldPose
```

You iterate through the array of matrices and combine the pose with the inverse bind transform.

➤ Open Model.swift and add this code to update(deltaTime:) after setting currentTime at the top of the method:

```
if let skeleton,
  let animation = animationClips.first {
  let animationClip = animation.value
  skeleton.updatePose(
    at: currentTime,
    animationClip: animationClip)
}
```

<a id="page-623"></a>

With that done, you have completed calculating the skeleton’s current pose for the frame.

![Figure](Metal_by_Tutorials_v500mpdf/aa11795680bcc512d12fa42d.png)

_The final pose_

Note: Currently USDZ files only hold one animation. Apple suggests, with some judicious coding, you could load multiple USDZ files, one with the geometry and skeleton, and others with solely the animation.

## **4. Update the Joint Matrix Palette Buffer**

➤ Open **Skin.swift** and examine the structure.

The initialization creates an MTLBuffer ready to hold the matrix for the joints. Skin holds only those joint paths for the current Mesh, so you create a skin-to-skeleton map to retrieve the correct pose from the skeleton’s array of joint matrices.

➤ Add the following method to Skin:

```
func updatePalette(skeleton: Skeleton?) {
  guard let skeletonPose = skeleton?.currentPose
    else { return }
  var palettePointer =
jointMatrixPaletteBuffer.contents().bindMemory(
    to: float4x4.self,
    capacity: jointPaths.count)
  for index in 0..<jointPaths.count {
    let skinIndex = skinToSkeletonMap[index]
    palettePointer.pointee = skeletonPose[skinIndex]
    palettePointer = palettePointer.advanced(by: 1)
```

<a id="page-624"></a>

```
  }
}
```

You initialize the buffer pointer and bind the contents of the buffer to an array of 4x4 matrices. You then iterate through the joint paths, retrieving the joint’s pose from the skeleton’s array of joint matrices, and storing them into the Metal buffer.

➤ Open Model.swift, and in update(deltaTime:), replace the existing animation code:

```
for index in 0..<meshes.count {
  meshes[index].transform?.getCurrentTransform(at: currentTime)
}
```

➤ With:

```
for index in 0..<meshes.count {
  var mesh = meshes[index]
  mesh.transform?.getCurrentTransform(at: currentTime)
  mesh.skin?.updatePalette(skeleton: skeleton)
  meshes[index] = mesh
}
```

On each frame for each mesh, you update the skin’s joint palette matrix

## **Joints and Weights Vertex Data**

Each vertex is weighted to up to four joints. You saw this in the earlier elbow example, where some vertices belonging to the lower arm joint would get 50% of the upper arm joint’s rotation. Soon, you’ll change the default vertex descriptor to load vertex buffers with four joints and four weights for each vertex.

The vertex function will sample from the joint matrix palette, and, using the weights, will apply the transformation matrix to each vertex. The following image shows a vertex that is assigned 50% to joint 2 and 50% to joint 3.

<a id="page-625"></a>

The other two joint indices are unused.

![Figure](Metal_by_Tutorials_v500mpdf/f94c4ffe3ca173ba4535b944.png)

After multiplying the vertex by the projection, view and model matrices, the vertex function will multiply the vertex by a weighting of each of the joint transforms. Using the example in the image above, the weighting will be 50% of Bone 2’s joint matrix and 50% of Bone 3’s joint matrix.

## **Transfer the Data to the GPU**

All of the meshes are now in position and ready to render.

➤ Open Rendering.swift in the Renderer folder, and in render(encoder:uniforms:params:), at the top of the loop for mesh in meshes, add this:

```
if let paletteBuffer = mesh.skin?.jointMatrixPaletteBuffer {
  encoder.setVertexBuffer(
    paletteBuffer,
    offset: 0,
    index: JointBuffer.index)
}
```

You set up the joint matrix palette buffer so that the GPU can read it. The vertex shader function will apply the matrices in the palette to the vertices.

➤ In the Shaders folder, open ShaderDefs.h, and add two attributes to VertexIn:

```
ushort4 joints [[attribute(Joints)]];
float4 weights [[attribute(Weights)]];
```

The attribute constants Joints and Weights were set up for you in the starter project in Common.h in Attributes.

<a id="page-626"></a>

To match VertexIn, you’ll need to update Model’s vertex descriptor.

➤ Open VertexDescriptor.swift, and uncomment the two extra vertex attributes for joints and weights. Model I/O, when loading the file, will now load joint index and joint weight information to the model’s vertex buffers.

Your vertex buffer layout will now look like this:

![Figure](Metal_by_Tutorials_v500mpdf/a278902f58d8774b2d77edcf.png)

_Vertex Buffer 0_

➤ Build and run the app to ensure that everything still works:

![Figure](Metal_by_Tutorials_v500mpdf/d929a097f7f5ed05a6a80f68.png)

_No obvious changes yet_

There are no obvious changes, but with a little bit of matrix multiplication, Skelly will be waving soon.

## **Updating the Vertex Shader**

➤ In the Shaders folder, open Vertex.metal, and add a new parameter to vertex\_main:

`constant float4x4 *jointMatrices [[buffer(JointBuffer)]]`

<a id="page-627"></a>

➤ Replace the entire contents of `vertex_main` with:

```
bool hasSkeleton = true;
float4 position = in.position;
float4 normal = float4(in.normal, 0);
```

Some models will have skeletons and joint matrices, but others, such as the ground plane won’t. You’ll have to set up a conditional to determine which type of model you are rendering. For the moment you assume that all models have a joint matrix palette.

➤ After the code you just added, add the following code to combine the joint matrix and weight data with the position and normal:

```
if (hasSkeleton) {
  float4 weights = in.weights;
  ushort4 joints = in.joints;
  position =
      weights.x * (jointMatrices[joints.x] * position) +
      weights.y * (jointMatrices[joints.y] * position) +
      weights.z * (jointMatrices[joints.z] * position) +
      weights.w * (jointMatrices[joints.w] * position);
  normal =
      weights.x * (jointMatrices[joints.x] * normal) +
      weights.y * (jointMatrices[joints.y] * normal) +
      weights.z * (jointMatrices[joints.z] * normal) +
      weights.w * (jointMatrices[joints.w] * normal);
}
```

You take each joint to which the vertex is bound, calculate the final position and normal, and then take the weighted part of that calculation.

If the function constant hasSkeleton is false, you’ll just use the original position and normal.

➤ Add the `VertexOut out` assignment:

```
float4 worldPosition = uniforms.modelMatrix * position;
VertexOut out {
  .position = uniforms.projectionMatrix * uniforms.viewMatrix
                * uniforms.modelMatrix * position,
  .uv = in.uv,
  .worldPosition = worldPosition.xyz / worldPosition.w,
  .worldNormal = uniforms.normalMatrix * normal.xyz,
  .worldTangent = 0,
  .worldBitangent = 0
};
return out;
```

<a id="page-628"></a>

You use position and normal instead of in.position and in.normal. You should also pre-multiply the tangent and bitangent properties in the same way as normal, but for brevity, you set worldTangent and worldBitangent properties to zero.

➤ Build and run the app, and Skelly will now wave at you.

![Figure](Metal_by_Tutorials_v500mpdf/c676c82962b7ba0e78ad5e7c.png)

_Skelly waving_

The ground doesn’t render because vertex\_main always multiplies position by weights, and the ground doesn’t have joints or weights. All the ground vertices are rendered at position (0, 0, 0).

Of course you’ll want to render the ground, so you’ll tell the GPU pipeline that it has to conditionally prepare two different vertex functions, depending on whether the mesh has a skeleton or not.

Note: You may get a run time error: failed assertion Draw Errors Validation Vertex Function(vertex\_main): missing buffer binding at index 15 for jointMatrices[0], because you’re rendering the ground, which doesn’t have any joint matrices. In this case, open GameScene.swift, and in init(), temporarily change models = [ground, skeleton] to models = [skeleton] to see Skelly waving.

<a id="page-629"></a>

## **Function Specialization**

Over the years there has been much discussion about how to render conditionally. For example, in your fragment shaders when rendering textures, you use the Metal Shading Language function is\_null\_texture(textureName) to determine whether to use the value from the material or a texture.

To test whether or not you have a joint matrix, you don’t have a convenient MSL function.

Should you create separate short fragment shaders for different conditionals? Or should you have one long “uber” shader with all of the possibilities listed conditionally? Function specialization deals with this problem, and allows you to create one shader that the compiler turns into separate shaders.

When you create the model’s pipeline state, you set the Metal functions in the Metal Shading library, and the compiler packages them up. At this stage, you can create properties, and assign them index numbers to deal with conditional states. You can then pass these properties to the Metal library when you create the shader functions. The compiler will examine the functions and generate specialized versions of them.

In the shader file, you reference the properties by their index numbers.

![Figure](Metal_by_Tutorials_v500mpdf/d671db7566cd8f87e4ac44ba.png)

_Function constants_

➤ In the Render Passes folder, open Pipelines.swift.

You’ll first create a set of function constant values that will indicate whether to render with animation.

<a id="page-630"></a>

➤ Add this new method to PipelineStates:

```
static func makeFunctionConstants(hasSkeleton: Bool)
  -> MTLFunctionConstantValues {
  let functionConstants = MTLFunctionConstantValues()
  var property = hasSkeleton
  functionConstants.setConstantValue(
    &property,
    type: .bool,
    index: 0)
  return functionConstants
}
```

MTLFunctionConstantValues is a set that contains a Boolean value depending on whether a skeleton exists. You defined a Boolean value here, but values can be any type specified by MTLDataType. On the GPU side, you’ll soon create a Boolean constant using the same index value. In functions that use these constants, you can conditionally perform tasks.

➤ Change the signature of `createForwardPSO()` to:

```
static func createForwardPSO(hasSkeleton: Bool = false)
  -> MTLRenderPipelineState {
```

➤ At the top of createForwardPSO(hasSkeleton:), change the assignment to vertexFunction to:

```
let functionConstants =
  makeFunctionConstants(hasSkeleton: hasSkeleton)
let vertexFunction = try? Renderer.library?.makeFunction(
  name: "vertex_main",
  constantValues: functionConstants)
```

Here, you tell the compiler to create a library of functions using the function constants set. The compiler creates multiple shader functions and optimizes any conditionals in the functions.

Currently, you set the same standard pipeline state for all models in ForwardRenderPass. Generally, when you have any complexity, you’ll have to work out a system appropriate for your app to manage all your various pipeline states. You could use function specialization where possible, or create different vertex and fragment functions.

<a id="page-631"></a>

In this app, the time when you know whether your model has a skeleton or not, is when you load Model.

➤ Open Model.swift, and add a new property to Model:

`var pipelineState: MTLRenderPipelineState!`

➤ Add the following code to the end of init(name:):

```
let hasSkeleton = skeleton != nil
pipelineState =
  PipelineStates.createForwardPSO(hasSkeleton: hasSkeleton)
```

When you load the model, you’ll create a pipeline state with the appropriate vertex function.

➤ Open Rendering.swift, and at the top of render(encoder:uniforms:params:), add this:

`encoder.setRenderPipelineState(pipelineState)`

Each time you render a model, you’ll load the appropriate pipeline state object. As long as you do the creation of the pipeline states at the start of your app, they are lightweight to swap in and out.

Now for the GPU side!

➤ Open **Vertex.metal**, and add this code after the `import` statement:

`constant bool hasSkeleton [[function_constant(0)]];`

The function constant index matches the constant you just created in the MTLFunctionConstantValues set.

➤ In the `vertex_main` header, change the `jointMatrices` parameter to:

```
constant float4x4 *jointMatrices [[
  buffer(JointBuffer),
  function_constant(hasSkeleton)]]
```

<a id="page-632"></a>

You’ll have two different vertex\_mains in your Metal shader library, one for each condition of hasSkeleton. One vertex\_main will have jointMatrices as a parameter, if hasSkeleton is true, and the other won’t have that parameter at all.

➤ In `vertex_main`, remove:

`bool hasSkeleton = true;`

You use the pipeline constant in place of the local one.

Your animation may glitch because of synchronization issues. You’ll consider how to optimize your CPU / GPU synchronization in Chapter 30, “Profiling”.

➤ For the moment, open Renderer.swift, and at the end of draw(scene:in:), add this:

`commandBuffer.waitUntilCompleted()`

The thread will be blocked until the command buffer has finished executing all its commands.

➤ Build and run the app, and you’ll see your full scene of waving Skelly and static ground.

![Figure](Metal_by_Tutorials_v500mpdf/4dcac1b6491ec3f8a973da11.png)

<a id="page-633"></a>

## **Key Points**

• Character animation differs from transform animation. With transform animation, you deform the mesh directly. When animating characters, you use a skeleton with joints. The geometry mesh is attached to these joints and deforms when you rotate a joint.

• The skeleton consists of a hierarchy of joints. When you rotate one joint, all the child joints move appropriately.

• You attach the mesh to joints by weight painting in a 3D app. Up to four joints can influence each vertex (this is a limitation in your app, but generally weighting four joints is ample).

• Animation clips contain transformation data for keyframes. The app interpolates the transformations between keyframes.

• Each joint has a bind matrix, which, when applied, moves the joint to the origin.

• When your shaders have different requirements depending on different situations, you can use function specialization. You indicate the different requirements in the pipeline state, and the compiler creates multiple versions of the shader function.

## **Where to Go From Here?**

This chapter took you through the basics of character animation. But don’t stop there! There are so many different topics that you can investigate. For instance, you can:

• Download and render the animated toy drummer and biplane from Apple’s AR Quick Look Gallery (https://developer.apple.com/augmented-reality/quick-look/).

• Download USDZ models from http://sketchfab.com and see what works and what doesn’t. (Not all models will work, as not all rigging scenarios are taken care of in this chapter.)

• Learn how to animate your own characters in Blender and import them into your renderer. Start off with a simple robot arm, and work upward from there.

• Watch Disney and Pixar movies… call it research. No, seriously! Animation is a skill all of its own. Watch how people move; good animators can capture personality in a simple walk cycle.

<a id="page-634"></a>

# 25

# Chapter 25: Managing Resources

So far, you’ve created an engine where you can load complex models with textures and materials, animate or update them per frame and render them. Your scenes will start to get more and more complicated as you develop your game, and you’ll want to find more performant ways of doing things and organizing your game resources.

Instead of processing each submesh and laboriously moving each of the submesh’s textures to the GPU, you’ll take advantage of the centralization of your textures in the Texture Controller. By the end of the chapter, you’ll be able to move all your textures to the GPU at once with just one render encoder command.

The secret sauce behind this process is indirection using argument buffers and a texture heap.

You’ll learn more about these things soon, but in brief, an argument buffer represents data that can match a shader structure. You can send the argument buffer to a shader function with one command, instead of sending each of the structure components individually.

![Figure](Metal_by_Tutorials_v500mpdf/2fc2d015b794fe7ea71e88df.png)

_An argument buffer containing resources_

<a id="page-635"></a>

A heap is exactly what it sounds like. You gather up your resources, such as textures and buffers, into an area of memory called a heap. You can then send this heap to the GPU with one command.

![Figure](Metal_by_Tutorials_v500mpdf/c9fa0c6e8bd6a523ff78c7a6.png)

_A heap containing textures_

## **The Starter Project**

With the basic idea under your belt, you’re ready to get started.

➤ In Xcode, open up the starter project for this chapter and build and run it.

![Figure](Metal_by_Tutorials_v500mpdf/6c122d6e61036002b5cd6541.png)

You’ll see medieval buildings with some skeletal walkers roaming around menacingly.

<a id="page-636"></a>

The project consolidates many of the features that you’ve learned so far:

• Shadows

• IBL Lighting with sky box

• Animation

• Alpha testing

• Textured models

• Models with materials but no textures

There are a few added nifty features:

1. Shadows are now soft shadows with PCF filtering.

2. In the Textures folder, in TextureController.swift, TextureController has an extra level of indirection. The old textures dictionary is now named textureIndex and it holds indices into an array of textures.

![Figure](Metal_by_Tutorials_v500mpdf/313aad706b47deea73afbe9f.png)

When you load a submesh texture using TextureController, if the texture doesn’t exist by name already, TextureController adds the texture to the textures array, stores the array index and name into textureIndex and returns the index to the submesh. If the texture already exists by name, then the submesh simply holds the existing array index to the texture.

<a id="page-637"></a>

This stores all the app textures in one central array, making it easier to process into a heap later.

3. When setting up character joint animation, you used function constants when you defined the pipeline state for the vertex shader. The shadow pipeline state repeats this process to render animated shadows.

4. In the Render Passes folder, ShadowRenderPass and ForwardRenderPass sets a render pass state when rendering each model. The model then sets the correct mesh pipeline state depending on this render pass state, whether it is shadow or main.

## **Argument Buffers**

When rendering a submesh, you currently send up to six textures and a material individually to the GPU for the fragment shader: Base color, normal, roughness, metalness, ambient occlusion and opacity textures. During the frame render loop, each of the textures requires a renderEncoder.setFragmentTexture(texture:at:) command.

![Figure](Metal_by_Tutorials_v500mpdf/8c68d01e55f3efd62e273582.png)

_A barrel draw call_

All the textures have a purple exclamation mark, indicating that there is an inefficiency problem with the texture. In this case, the bindings are actually redundant because the textures have previously been bound in this render pass.

<a id="page-638"></a>

Using argument buffers, you can set pointers, defined as MTLResourceIDs, to these six textures in one buffer, and set this buffer on the render command encoder with just one command. This argument buffer doesn’t only have to point to textures, it can point to any other data necessary to render the frame.

![Figure](Metal_by_Tutorials_v500mpdf/793b6c2b5ee5561dd0032a95.png)

When you come to draw call time, instead of setting the textures on the render command encoder, you set the single argument buffer. You then perform renderEncoder.useResource(\_:usage:) for each texture so that you can access all six textures on the GPU as reusable indirect resources.

Once you set up an argument buffer, you can refer to it in a shader, using one structure that matches the buffer data as a parameter to the shader function.

During the render loop, setting textures and buffers on the render command encoder incurs some internal verification. This verifying process will now take place during initialization, when the texture and buffer resource ID pointers are initially set into the argument buffer. Anything you can move outside of the render loop is a gain.

## **Creating the Shader Structure**

➤ In the Shaders folder, open IBL.metal.

The fragment\_IBL function has six parameters for material textures and one for the Material. You’re going to combine all of these into one structure, and use the structure as the parameter.

➤ Open Material.h. This file contains the Material structure and texture index numbers. In previous chapters, these were in Common.h. You’ll need to access Material in Swift, so the bridging header file Common.h imports Material.h.

When you set up the argument buffer in Swift, you’ll store MTLResourceIDs. The fragment shader will expect texture2d&lt;float&gt;s.

<a id="page-639"></a>

You’ll now create structures that will work for both Swift and Metal Shading Language.

➤ Still in **Material.h**, before `#endif`, create a new structure:

```
#if __METAL_VERSION__
// MARK: - Metal Shading Language

#include <metal_stdlib>
using namespace metal;

struct ShaderMaterial {
  array<texture2d<float>, MaterialTextureCount> textures;
  Material material;
};

#endif // Metal version
```

There are six textures, and MaterialTextureCount is defined in TextureIndices as OpacityTexture (5) + 1.

➤ For the Swift side, add this code before #endif // Metal version:

```
#else
// MARK: - Swift side
#include <Metal/Metal.h>

struct ShaderMaterial {
  MTLResourceID textures[MaterialTextureCount];
  Material material;
};
```

Here, you make the equivalent declaration for Swift. Metal.h holds the necessary definition of MTLResourceID.

Each argument buffer structure element has an implicit ID. For example, textures[BaseColor] has an implicit ID of 0 here. If you want to use an out-of-order ID index, instead of defining the array, you can list all textures with explicit IDs with an attribute, for example: MTLResourceID baseColorTexture [[id(BaseColor)]].

Soon, you’ll create an argument buffer that matches these IDs. You’ll pass in material as a constant value. If you were to create an MTLBuffer containing material, you can define it in ShaderMaterial as: constant Material &amp;material;.

<a id="page-640"></a>

➤ Open **IBL.metal**, and change the signature for `fragment_IBL` to:

```
fragment float4 fragment_IBL(
  VertexOut in [[stage_in]],
  constant Params &params [[buffer(ParamsBuffer)]],
  constant Light *lights [[buffer(LightBuffer)]],
  constant ShaderMaterial &shaderMaterial
[[buffer(MaterialBuffer)]],
  depth2d<float> shadowTexture [[texture(ShadowTexture)]],
  texturecube<float> skybox [[texture(SkyboxTexture)]],
  texturecube<float> skyboxDiffuse
[[texture(SkyboxDiffuseTexture)]],
  texture2d<float> brdfLut [[texture(BRDFLutTexture)]])
```

Instead of receiving the textures directly, fragment\_IBL will receive just one structure containing all the textures and material needed for the model.

➤ Replace:

`Material material = _material;`

➤ With:

```
Material material = shaderMaterial.material;
auto textures = shaderMaterial.textures;
texture2d<float> baseColorTexture = textures[BaseColor];
texture2d<float> normalTexture = textures[NormalTexture];
texture2d<float> metallicTexture = textures[MetallicTexture];
texture2d<float> roughnessTexture = textures[RoughnessTexture];
texture2d<float> aoTexture = textures[AOTexture];
texture2d<float> opacityTexture = textures[OpacityTexture];
```

You remove all the compile errors with these assignments.

For the moment you’ve finished setting up the GPU shader.

## **Creating the Argument Buffer**

Now you’ll set up the argument buffer containing all the texture resource IDs in Swift.

➤ In the Geometry folder, open Submesh.swift, and add the new argument buffer property to Submesh:

`var materialBuffer: MTLBuffer!`

`materialBuffer` will contain pointers to the textures and the material.

<a id="page-641"></a>

➤ Create a new method in Submesh:

```
mutating func initializeMaterials() {
  // 1
  let materialBufferSize = MemoryLayout<ShaderMaterial>.stride
  materialBuffer = Renderer.device.makeBuffer(
    length: materialBufferSize)
  materialBuffer.label = "Material Buffer"
  // 2
  let textureIDs = allTextures.map { texture in
    texture?.gpuResourceID ?? MTLResourceID()
  }
  // 3
  let pointer = materialBuffer.contents()
    .assumingMemoryBound(to: ShaderMaterial.self)
  // 4
  pointer.pointee.material = material
  pointer.pointee.textures.0 = textureIDs[0]
  pointer.pointee.textures.1 = textureIDs[1]
  pointer.pointee.textures.2 = textureIDs[2]
  pointer.pointee.textures.3 = textureIDs[3]
  pointer.pointee.textures.4 = textureIDs[4]
  pointer.pointee.textures.5 = textureIDs[5]
}
```

Going through the code:

1. Create an MTLBuffer to hold the materials. Swift recognizes the ShaderMaterial structure that you set up in Material.h.

2. Create an array of MTLResourceIDs that match the submesh textures.

3. Create a pointer into the material buffer mapped to the ShaderMaterial structure.

4. Load up the data into the buffer. Unfortunately, arrays in Metal Shading Language are not dynamic. They have a fixed number of elements. Swift treats fixed arrays as tuples.

➤ Add the following code to the end of init(mdlSubmesh:mtkSubmesh:):

`initializeMaterials()`

In your app, there’s one other method where you can change textures.

➤ Open Model.swift and add this at the end of setTexture(name:type:):

`meshes[0].submeshes[0].initializeMaterials()`

<a id="page-642"></a>

You call setTexture(name:type:) when you set the texture on the ground plane primitive.

You’ve now set up your argument buffer. Instead of setting the textures and material for the fragment shader during the render loop, you’ll be able to set the single argument buffer.

## **Updating the Draw Call**

➤ In the Renderer folder, open Rendering.swift. This holds the extension on Model, where you render each model.

➤ In render(encoder:uniforms:params:renderState:), in the for submesh in mesh.submeshes loop, locate  setMaterials(encoder:submesh:).

setMaterials(encoder:submesh:) encodes all the textures and materials to the fragment function. As you’re now using one buffer for all these textures and materials, this method is no longer necessary.

➤ Replace:

`setMaterials(encoder: encoder, submesh: submesh)`

➤ With:

```
encoder.setFragmentBuffer(
  submesh.materialBuffer,
  offset: 0,
  index: MaterialBuffer.index)
```

Instead of encoding all of the textures, you simply send the single argument buffer to the GPU.

Don’t build and run now. But if you did, you might get a lot of GPU errors appearing in the debug console:

![Figure](Metal_by_Tutorials_v500mpdf/6b1e25ffe9c7d5f87827ca34.png)

_GPU errors_

<a id="page-643"></a>

Even if the render appears correct, if you capture the GPU workload, you might still get errors. When you have GPU memory errors, weird things can happen on the display. Debugging these errors can be frustrating as your display may lock up because you have accessed memory that you’re not supposed to.

In this case, running on iPad Air 3, the textures are either missing or pink. On the buildings, the colors come from material.baseColor.

![Figure](Metal_by_Tutorials_v500mpdf/6e36eb17fd4df8adca61338a.png)

_GPU errors_

You’ve set up a level of indirection with the argument buffer pointing to the textures, but you still have to tell the GPU to load these textures. When dealing with indirection and buffer data, it’s often easy to omit this vital step, so if you have errors at any time, check in the GPU debugger that the resource is available in the indirect resource list, but also check that you are using the resource in the render command encoder command list.

➤ Still inside the conditional if renderState != .shadowPass, but after the previous code, add this:

```
submesh.allTextures.forEach { texture in
  if let texture {
    encoder.useResource(texture, usage: .read,
stages: .fragment)
  }
}
```

Here, you tell the GPU that you’re going to read from these textures, and they should be resident on the GPU available to fragment shaders.

➤ Delete the method setMaterials(encoder:submesh:) since you no longer need it.

<a id="page-644"></a>

➤ Build and run the app, and the scene will render as before.

![Figure](Metal_by_Tutorials_v500mpdf/fe7360c27f90aad80858c72c.png)

_Using argument buffers_

➤ Capture the GPU workload.

➤ In the Debug navigator, open Command Buffer and Forward Render Pass and select ground.

➤ Select Bound Resources using the navigator icon at the top left of the pane and examine the resources.

![Figure](Metal_by_Tutorials_v500mpdf/51c5f012c4d6339217188290.png)

_Indirect Resources_

<a id="page-645"></a>

For the ground plane, the Indirect section lists the color texture grass. MTLRenderCommandEncoder.useResource(\_:usage:) explicitly makes the texture accessible to the GPU as an indirect resource.

➤ Under **Fragment**, double-click **Material Buffer** to examine it.

Note: It’s important to label buffers so that you can recognize what they are in the GPU capture. Because you labelled Material Buffer when you created it, the buffer isn’t called something like Buffer 0x840ab180.

![Figure](Metal_by_Tutorials_v500mpdf/e40031b3ca64d01be19c0557.png)

_Ground plane textures_

Here, you can examine the textures and material properties in shaderMaterial. The ground doesn’t have a normal texture.

The arrow next to grass indicates the indirection. If you click the arrow, you’ll see the ground plane’s color texture with mip maps.

You’ve now set up your app to use argument buffers for textures and the material instead of sending them individually. This may not feel like a win yet, and you’ve increased overhead by adding a new buffer. But you’ve reduced overhead on the render command encoder. Instead of having to validate the textures each frame, the textures are validated when they are first placed into the argument buffer, while you’re still initializing your app data.  In addition to this, you’re grouping your materials together into the one structure, and only using one argument table entry in the fragment function. If you have many parameters that you can group together, this will save resources.

<a id="page-646"></a>

## **Resource Heaps**

You’ve grouped textures into an argument buffer for each submesh, but you can also combine all your app’s textures into a resource heap.

![Figure](Metal_by_Tutorials_v500mpdf/7afa3319c6a2d0d3426c23d2.png)

A resource heap is simply an area of memory where you bundle resources. These can be textures or data buffers. To make your textures available on the GPU, instead of having to perform renderEncoder.useResource(\_:usage:) for every single texture, you can perform renderEncoder.useHeap(\_:) once per frame instead. That’s one step further in the quest for reducing render commands.

Note: The following code is not optimized. You will create the MTLTexture twice. Once on loading, and then you’ll copy it to the heap as a new texture. This is the easiest way to include the process in your app, but you can work on loading techniques where you pre-load static mesh and textures straight into heaps.

<a id="page-647"></a>

➤ In the Textures folder, open TextureController.swift.

TextureController stores all your app’s textures in one central array: textures. From this array, you’ll gather all the textures into a heap and move the whole heap at one time to the GPU.

➤ In `TextureController`, create a new property:

`static var heap: MTLHeap?`

➤ Create a new type method to build the heap:

```
static func buildHeap() -> MTLHeap? {
  let heapDescriptor = MTLHeapDescriptor()

  // add code here

  guard let heap =
    Renderer.device.makeHeap(descriptor: heapDescriptor)
    else { return nil }
  return heap
}
```

MTLDevice.makeHeap(descriptor:) is a time-consuming operation, so make sure that you execute it at loading time, rather than when your app is in full swing. Once you’ve created the heap, it’s fast to add Metal buffers and textures to it.

You build a heap from a heap descriptor. This descriptor will need to know the size of all the textures combined. Unfortunately MTLTexture doesn’t hold that information, but you can retrieve the size of a texture from a texture descriptor.

In the Utility folder, in Extensions.swift, there’s an extension on MTLTexture that will provide a descriptor from the texture.

➤ In **TextureController.swift**, in `buildHeap()`, replace `// add code here` with:

```
let descriptors = textures.map { texture in
  texture.descriptor
}
```

Here, you create an array of texture descriptors to match the array of textures. Now you can add up the size of all these descriptors.

<a id="page-648"></a>

➤ Following on from the previous code, add this:

```
let sizeAndAligns = descriptors.map { descriptor in
  Renderer.device.heapTextureSizeAndAlign(descriptor:
descriptor)
}
heapDescriptor.size = sizeAndAligns.reduce(0) { total,
sizeAndAlign in
  let size = sizeAndAlign.size
  let align = sizeAndAlign.align
  return total + size - (size & (align - 1)) + align
}
if heapDescriptor.size == 0 {
  return nil
}
```

You calculate the size of the heap using size and correct alignment within the heap. As long as align is a power of two, (size &amp; (align - 1)) will give you the remainder when size is divided by alignment. For example, if you have a size of 129 bytes, and you want to align it to memory blocks of 128 bytes, this is the result of size - (size &amp; (align - 1)) + align:

`129 - (129 & (128 - 1)) + 128 = 256`

This result shows that if you want to align blocks to 128, you’ll need a 256 byte block to fit 129 bytes.

You have an empty heap, but you need to populate it with textures. Each texture must match the heap’s CPU cache mode and also the heap’s storage mode.

➤ At the end of `buildHeap()`, but before `return heap`, add this:

```
let heapTextures = descriptors.map { descriptor -> MTLTexture in
  descriptor.storageMode = heapDescriptor.storageMode
  descriptor.cpuCacheMode = heapDescriptor.cpuCacheMode
  guard let texture = heap.makeTexture(descriptor: descriptor)
else {
    fatalError("Failed to create heap textures")
  }
  return texture
}
```

You iterate through the descriptors array and create a texture for each descriptor. You store this new texture in heapTextures.

heapTextures now contains a bunch of empty texture resources. To copy the submesh texture information to the heap texture resources, you’ll need a blit command encoder.

<a id="page-649"></a>

## **The Blit Command Encoder**

To blit means to copy from one part of memory to another and is typically an extremely fast operation. You create a blit command encoder using a command buffer, just as you did the render and compute command encoders. You then use this encoder when you want to copy a resource such as a texture or Metal buffer.

➤ Add this after the previous code, before return heap:

```
guard
  let commandBuffer = Renderer.commandQueue.makeCommandBuffer(),
  let blitEncoder = commandBuffer.makeBlitCommandEncoder()
else { return nil }
  zip(textures, heapTextures)
  .forEach { texture, heapTexture in
    heapTexture.label = texture.label
    // blit here
  }
```

You create the blit command encoder using a command buffer. You then set up a forEach loop that will process all the textures and match them with the heap textures.

➤ Replace `// blit here` with:

```
var region =
  MTLRegionMake2D(0, 0, texture.width, texture.height)
for level in 0..<texture.mipmapLevelCount {
  for slice in 0..<texture.arrayLength {
    blitEncoder.copy(
      from: texture,
      sourceSlice: slice,
      sourceLevel: level,
      sourceOrigin: region.origin,
      sourceSize: region.size,
      to: heapTexture,
      destinationSlice: slice,
      destinationLevel: level,
      destinationOrigin: region.origin)
  }
  region.size.width /= 2
  region.size.height /= 2
}
```

When copying textures, you specify a region. Initially the region will be the entire texture’s width and height. You’ll then blit mip levels where the region will get progressively smaller.

<a id="page-650"></a>

You copy each texture to a heap texture. Within each texture, you copy each level and slice. Levels contain the texture mipmaps, which is why you halve the region each loop. A slice is either the index into a texture array, or, for a cube texture, one of six cube faces.

Even though there are a lot of parameters to the blit encoder copy method, they are simply for deciding which area of the texture is to be copied. You can copy part of a texture by setting the origin and source size of the region. You can also copy part of a texture to a different region in the destination texture.

➤ Before `return heap`, add the following:

```
blitEncoder.endEncoding()
commandBuffer.commit()
Self.textures = heapTextures
```

This ends the encoding, commits the command buffer and replaces the original textures with the heap textures. TextureController.buildHeap() will now create a heap from all the textures gathered during scene loading.

➤ In the Geometry folder, open Submesh.swift.

In initializeMaterials(), you create an argument buffer from the submesh textures when you load the submesh. Unfortunately, as you’ve now copied all the old textures to new heap textures, your submesh argument buffers point to the wrong textures now.

➤ At the end of `init(mdlSubmesh:mtkSubmesh:)`, remove:

`initializeMaterials()`

Open **Model.swift**, and in `setTexture(name:type:)`, remove:

`meshes[0].submeshes[0].initializeMaterials()`

You’ll need to create the argument buffers after you’ve created the heap.

➤ In the Renderer folder, open Renderer.swift, and add a new method to Renderer:

```
func initialize(_ scene: GameScene) {
  TextureController.heap = TextureController.buildHeap()
  for model in scene.models {
    model.meshes = model.meshes.map { mesh in
      var mesh = mesh
      mesh.submeshes = mesh.submeshes.map { submesh in
```

<a id="page-651"></a>

```
        var submesh = submesh
        submesh.initializeMaterials()
        return submesh
      }
      return mesh
    }
  }
}
```

initialize(\_:) will ensure that the heap gets built before the main render loop. You then process all the submeshes and initialize the materials with the correct textures.

➤ In the Game folder, open GameController.swift, and in init(metalView:options:) after scene = GameScene(),add this:

`renderer.initialize(scene)`

➤ Build and run the app to ensure that everything still works.

![Figure](Metal_by_Tutorials_v500mpdf/7e7a5692e762ecf7354ab175.png)

_Skeletons on parade_

You’ve now placed all your textures in a heap, and are using those individual textures, but aren’t yet taking full advantage of the heap. Before rendering any models, you can send the textures to the GPU at the start of a render pass to be all ready and waiting for processing.

➤ In the Render Passes folder, open ForwardRenderPass.swift.

➤ In draw(commandBuffer:scene:uniforms:params:), add this after creating renderEncoder:

`if let heap = TextureController.heap {`

<a id="page-652"></a>

```
  renderEncoder.useHeap(heap, stages: .fragment)
}
```

➤ Open Rendering.swift, and in render(encoder:uniforms:params:renderState:), remove:

```
submesh.allTextures.forEach { texture in
  if let texture = texture {
    encoder.useResource(texture, usage: .read,
stages: .fragment)
  }
}
```

Instead of having a useResource command for every texture, you perform one useHeap every render pass. This could be a huge saving on the number of commands in a render command encoder, and so a reduction of the number of commands that a GPU has to process each frame.

➤ Build and run the app, and your render will be exactly the same as it was last time you ran the app.

![Figure](Metal_by_Tutorials_v500mpdf/974dc9a17a12adb68252eb5c.png)

_Rendering with a texture heap_

➤ Capture the GPU workload.

➤ Open Command Buffer &gt; Forward Render Pass and select the useHeap command that you set at the start of the render pass.

<a id="page-653"></a>

In the bound resources, all the scene textures are listed under indirect resources, and are available for use in any shader during this render pass.

![Figure](Metal_by_Tutorials_v500mpdf/ed77bcca1cf8ba24a2797f0d.png)

If you check out each of the models’ draw calls, you’ll also see that you reduced the number of encoded render commands along with most of the redundant bindings.

![Figure](Metal_by_Tutorials_v500mpdf/2abd6a7685c590393e31fe7a.png)

## **Residency Sets**

So far, you’ve moved your texture binding process from each submesh to each draw call. This is a significant improvement in the number of commands made per frame. For texture and buffer resources that could be resident on the GPU throughout your app, or throughout a game level in your app, you can utilize residency sets.

Residency sets allow you to load up a group of resources at one time, for example, at the start of a level, and then unload them at the end of the level.

<a id="page-654"></a>

You’ve created a heap which will avoid memory fragmentation, but you could bypass this step and add the textures to a residency set instead. Since you have the heap created already, you’ll add the heap to the residency set.

➤ In the Renderer folder, open Renderer.swift, and add a new property to Renderer:

`let residencySet: MTLResidencySet`

➤ In `init(metalView:options:)`, before `super.init`, initialize the residency set:

```
let setDescriptor = MTLResidencySetDescriptor()
setDescriptor.label = "Residency Set"
setDescriptor.initialCapacity = 1
residencySet = try! device.makeResidencySet(
  descriptor: setDescriptor)
```

You set the initial capacity of the set to one, because you know that you are only adding one resource, the heap, to the set. If you add resources directly to the set, you should pre-calculate how many there are. Apple documentation says you can leave this as zero, and Metal will give the residency set a “standard starting capacity”.

➤ In initialize(scene:), after building the heap, but before the for loop, add this code:

```
residencySet.addAllocation(TextureController.heap!)
residencySet.commit()
```

You add the heap to the residency set and indicate that you have finished adding and removing resources.

You now have the choice of attaching the residency set to a command buffer on each frame, or attaching it to the command queue once. Your meshes are static and used throughout your app, so you can attach the set to the command queue.

➤ After the previous code add this code:

`Renderer.commandQueue.addResidencySet(residencySet)`

Now, whenever you commit your command buffer during a frame, Metal will automatically attach the residency set to the command buffer, making the resources available to GPU shader functions.

➤ In the Render Passes folder, open ForwardRenderPass.swift, and, in draw(commandBuffer:scene:uniforms:params:), remove:

<a id="page-655"></a>

```
if let heap = TextureController.heap {
  renderEncoder.useHeap(heap, stages: .fragment)
}
```

As your heap is now in a residency set, you don’t need this extra command.

Build and run your app, and check that it still works.

![Figure](Metal_by_Tutorials_v500mpdf/754838ecf595968a1f02819f.png)

The residency set is now available when your app commits the command buffer.

![Figure](Metal_by_Tutorials_v500mpdf/face0e2e7aec2870ef3da89e.png)

You’ve now separated out binding your textures from your rendering code, with a level of indirection via the argument buffer. But have you seen any performance improvement? In this example, on a recent device, probably not. But the more complicated your render passes get, the better the improvement, as there will be better memory management and fewer render commands.

With the residency set, you have more control over when you can load and unload your set of textures.

<a id="page-656"></a>

## **Key Points**

• An argument buffer is a collection of pointers to resources that you can pass to shaders.

• A resource heap is a collection of textures or Metal buffers. A heap can be static, as in this chapter’s example, but you can also reuse space on the heap where you use different textures at different times.

• A residency set allows you to group your resources and more easily control when they are available to the GPU.

<a id="page-657"></a>

# 26

# Chapter 26: Indirect Command Encoding

Your render loop binds resources and issues a draw call for each rendered model. This process has worked well so far. Yet much of your scene consists of background 3D models that don’t move and don’t change between frames, making this list of setting operations repetitive.

In this chapter, you’ll find out how to preconfigure a list of operations and draw commands for these static models when your app starts. You’ll then be able to remove that long list from your render loop.

You may not see the immediate gains of indirect rendering on the CPU. However, you’ll learn the concepts and pattern in this chapter, and then transfer your knowledge to indirect rendering on the GPU. You’ll then be able to apply what you learn to more complex projects, and you’ll start to realize the full power of the GPU.

<a id="page-658"></a>

## **The Starter Project**

The GPU requires a lot of information to be able to render a model. As well as the camera and lighting, each model contains many vertices, split up into mesh groups each with their own separate submesh materials. The following image shows a house with at least five different submeshes:

![Figure](Metal_by_Tutorials_v500mpdf/c7644f169967abcd65e266f3.png)

_A house model with submeshes expanded_

The scene you’ll render, in contrast, will only render two static models, each with one mesh and one submesh. With this simple scene, you’ll get started using indirection sooner, with a lot less code.

<a id="page-659"></a>

➤ In Xcode, open the starter project, and build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/2e69e3ef3a501e212a49f197.png)

_The starter app_

The project contains only the bare minimum to render these two textured models. There are no shadows, transparency or lighting.

These are the important things to notice:

• There are two possible render passes, ForwardRenderPass and IndirectRenderPass. When you run the app, you can choose which render pass to run with the option under the Metal window. Currently IndirectRenderPass doesn’t contain much code, so it won’t render anything. IndirectRenderPass.swift is where you’ll add most of the code in this chapter.

• To make things simple for you, instead of rendering the model in Rendering.swift, the rendering code is all in ForwardRenderPass. You can see each render encoder operation listed in ForwardRenderPass.draw(commandBuffer:scene:uniforms). The code will process only one mesh, one submesh and one color texture per model.

• Up until now, you’ve changed Uniforms.modelMatrix and Params.tiling for every model. This isn’t strictly correct. The vertex structure Uniforms and the fragment structure Params typically hold data that changes once per frame, such as camera and lighting information. modelMatrix and tiling are per-object properties. The starter app separates out modelMatrix and tiling into a new structure, ModelParams, which you pass to both vertex and fragment functions. As you’re not doing any lighting, Params doesn’t exist in this app.

<a id="page-660"></a>

## **Indirect Command Buffers (ICB)**

This is a list of some of your operations in your current render loop:

```
encoder.setRenderPipelineState(...)
encoder.setVertexBuffer(...)
encoder.setFragmentBytes(...)
encoder.setFragmentBuffer(...)
encoder.drawIndexedPrimitives(...)
```

Since, for static models, these operations don’t need updating every frame, you can set up a list of rendering operations, during your app loading, in an Indirect Command Buffer, or ICB for short.

In your render loop, you can then issue one single execute command to your render command encoder, and all the bindings and commands in the ICB will transfer to the GPU.

Your rendering process currently looks like this:

![Figure](Metal_by_Tutorials_v500mpdf/70dcdcec71baed14169cc4c1.png)

_Your render loop_

You load all the model data, materials and pipeline states at the start of the app. For each render pass, you create a render command encoder and bind all the resources, one after another, to that encoder, ending with a draw call. You repeat the drawing process for each model.

As well as initializing all your resources at the start of the app, you’ll also initialize your render commands there too. You’ll set up each draw command with pointers to the relevant uniform, material and vertex buffers and specify how to do the draw. During the render loop, you can just issue one execute command to the render command encoder, and the encoder will send the list of commands, all at once, off to the GPU.

<a id="page-661"></a>

Your rendering process will then look like this:

![Figure](Metal_by_Tutorials_v500mpdf/54c379f74c2d6095d43a6ec9.png)

_Indirect rendering_

Remember that your aim is to do as much as you can when your app first loads, and as little as you have to per frame. To achieve this, you’ll:

1. Place your uniform data in a buffer. Unfortunately you can’t send ad hoc bytes to the GPU using an ICB, but you can still update the uniforms buffer each frame.

2. Set up an indirect command buffer. This buffer will hold all the draw commands.

3. Loop through the models, setting up the bindings in the indirect command buffer.

4. Ensure the resources are resident on the GPU.

5. Execute the command list.

That’s quite a todo list, so let’s get started!

## **1. Initializing the Uniform Buffer**

➤ In the Render Passes folder, open IndirectRenderPass.swift.

IndirectRenderPass contains the minimum code to conform to RenderPass. The pipeline is the same as that in the forward render pass, so it will call the same shader functions.

➤ Add a new property to IndirectRenderPass:

`var uniformsBuffer: MTLBuffer!`

You create a buffer that will hold the camera uniform data.

<a id="page-662"></a>

➤ Add the initializer method to IndirectRenderPass:

```
mutating func initializeUniforms() {
  let bufferLength = MemoryLayout<Uniforms>.stride
    uniformsBuffer =
  Renderer.device.makeBuffer(length: bufferLength, options: [])
  uniformsBuffer.label = "Uniforms"
}
```

➤ In the Geometry folder, open Model.swift and add a new buffer property to Model:

```
lazy var modelParamsBuffer: MTLBuffer = {
  let buffer = Renderer.device.makeBuffer(
    length: MemoryLayout<ModelParams>.stride)!
  buffer.label = "Model Parameters Buffer"
  return buffer
}()
```

Currently, in the render loop, you transfer ModelParams to the GPU as ad hoc bytes. Instead, you’ll hold the model matrix and tiling data in this buffer.

Even though the models are static, you’ll still have to update the camera uniforms every frame, in case the user has changed the camera position.

➤ Open IndirectRenderPass.swift and add this new method to IndirectRenderPass:

```
func updateUniforms(scene: GameScene, uniforms: Uniforms) {
  var uniforms = uniforms
  uniformsBuffer.contents().copyMemory(
    from: &uniforms,
    byteCount: MemoryLayout<Uniforms>.stride)
}
```

You load up the uniforms buffer with the current data for each frame.

➤ Call this method at the top of draw(commandBuffer:scene:uniforms:):

`updateUniforms(scene: scene, uniforms: uniforms)`

<a id="page-663"></a>

## **2. Setting up an Indirect Command Buffer (ICB)**

You’re now ready to create some indirect commands.

ICBs allow you to set three objects using command arguments:

• Pipeline State

• Vertex Buffer

• Fragment Buffer

➤ Open ForwardRenderPass.swift, and look at draw(commandBuffer:scene:uniforms:). Refresh your memory on where you use those three render operations in the render loop. You’re going to move these operations to an indirect command list and use buffers instead of setting vertex or fragment bytes.

➤ Open IndirectRenderPass.swift, and add a new property to IndirectRenderPass.

`var icb: MTLIndirectCommandBuffer!`

This buffer will hold the render command list.

➤ Create a new method in IndirectRenderPass:

```
mutating func initializeICBCommands(_ models: [Model]) {
  // 1
  let icbDescriptor = MTLIndirectCommandBufferDescriptor()
  // 2
  icbDescriptor.commandTypes = [.drawIndexed]
  // 3
  icbDescriptor.inheritBuffers = false
  // 4
  icbDescriptor.maxVertexBufferBindCount = 25
  icbDescriptor.maxFragmentBufferBindCount = 25
  // 5
  icbDescriptor.inheritPipelineState = true
}
```

Going through these settings:

1. You create an Indirect Command Buffer descriptor.

2. You specify that (eventually) the GPU should expect an indexed draw call. That’s a draw call that uses an index buffer for indexing into the vertices.

<a id="page-664"></a>

3. If you set inheritBuffers as true, you can only set the buffers on the render command encoder and not on the ICB.

4. You set the maximum number of buffers that the ICB can bind to in the vertex and fragment shader parameters to 25. This is far too many, but you can renumber the buffer indices when your app is complete.

5. You set inheritPipelineState to true. Because this app contains such simple models, you can set the render pipeline state at the start of the render pass, and all encoder commands will inherit the current pipeline state. If you require a different pipeline for different submeshes, you’d set inheritPipelineState to false and add setting the render pipeline state to the list of indirect encoder command bindings.

➤ At the end of `initializeICBCommands(_:)`, create the indirect command buffer:

```
guard let icb = Renderer.device.makeIndirectCommandBuffer(
  descriptor: icbDescriptor,
  maxCommandCount: models.count,
  options: []) else { fatalError("Failed to create ICB") }
self.icb = icb
```

The ICB will need one command per draw call. In this app, you’re only performing one draw call per model, but in a more complex app where you’re doing a draw call for every submesh, you’d have to iterate through the models prior to setting up the ICB to find out how many draw calls you’ll do.

## **3. Setting up the Model Bindings**

Now that you’ve set up an indirect command buffer, you’ll add the list of bindings to it.

➤ Add the following code to the end of initializeICBCommands(\_:):

```
for (modelIndex, model) in models.enumerated() {
  var modelParams = ModelParams(
    modelMatrix: model.transform.modelMatrix,
    tiling: model.tiling)
  model.modelParamsBuffer.contents().copyMemory(
    from: &modelParams,
    byteCount: MemoryLayout<ModelParams>.stride)
}
```

You iterate through the models and update each model’s buffer with its model matrix and tiling data.

<a id="page-665"></a>

➤ Continue adding code at the end of the `for` loop:

```
let mesh = model.meshes[0]
let submesh = mesh.submeshes[0]
let icbCommand = icb.indirectRenderCommandAt(modelIndex)
icbCommand.setVertexBuffer(
  uniformsBuffer, offset: 0, at: UniformsBuffer.index)
icbCommand.setVertexBuffer(
  model.modelParamsBuffer, offset: 0, at:
ModelParamsBuffer.index)
icbCommand.setFragmentBuffer(
  model.modelParamsBuffer, offset: 0, at:
ModelParamsBuffer.index)
icbCommand.setVertexBuffer(
  mesh.vertexBuffers[VertexBuffer.index],
  offset: 0,
  at: VertexBuffer.index)
icbCommand.setVertexBuffer(
  mesh.vertexBuffers[UVBuffer.index],
  offset: 0,
  at: UVBuffer.index)
icbCommand.setFragmentBuffer(
  submesh.materialBuffer, offset: 0, at: MaterialBuffer.index)
```

This code will look familiar to you from the render loop in ForwardRenderPass.draw(commandBuffer:scene:uniforms:). You set all the necessary data for each model’s draw call, keeping track of each draw command with modelIndex.

For setting the vertex buffers, it’s important to match how you formatted your vertex buffers when first loading the models.

➤ In the Geometry folder, open VertexDescriptor.swift, and examine how the vertex buffers are configured.

![Figure](Metal_by_Tutorials_v500mpdf/b0059f17cb73ef2a1d69c5cb.png)

_Vertex buffer layouts_

<a id="page-666"></a>

There are only two vertex buffers, as the vertex descriptor is simplified from previous chapters.

➤ Open IndirectRenderPass.swift, and add the draw call to the end of the previous for loop in initializeICBCommands(\_:):

```
icbCommand.drawIndexedPrimitives(
  .triangle,
  indexCount: submesh.indexCount,
  indexType: submesh.indexType,
  indexBuffer: submesh.indexBuffer,
  indexBufferOffset: submesh.indexBufferOffset,
  instanceCount: 1,
  baseVertex: 0,
  baseInstance: 0)
```

This draw command is very similar to the one that you’ve already been using. There are a couple of extra arguments:

• baseVertex: The vertex in the vertex buffer to start rendering from.

• baseInstance: The instance to start rendering from. You only have one instance of each model here.

The command list is now complete.

➤ In `IndirectRenderPass`, create a new method:

```
mutating func initialize(models: [Model]) {
  initializeUniforms()
  initializeICBCommands(models)
}
```

Here, you call the two methods that will initialize your buffers.

➤ In the Renderer folder, open Renderer.swift, and add this to the end of initialize(\_:):

`indirectRenderPass.initialize(models: scene.models)`

## **4. Making the Resources Resident on the GPU**

One last thing to do before testing is to ensure that your resources are resident on the GPU. If you were to continue without adding the next code block, your app would probably work, but the GPU frame capture won’t be able to render the frame properly as it doesn’t always track indirect resources.

<a id="page-667"></a>

➤ Open IndirectRenderPass.swift, and create a new method in IndirectRenderPass:

```
func useResources(
  encoder: MTLRenderCommandEncoder, models: [Model]
) {
  encoder.pushDebugGroup("Using resources")
  encoder.useResource(
    uniformsBuffer,
    usage: .read,
    stages: .vertex)
  for model in models {
    let mesh = model.meshes[0]
    let submesh = mesh.submeshes[0]
    [
      model.modelParamsBuffer,
      mesh.vertexBuffers[VertexBuffer.index],
      mesh.vertexBuffers[UVBuffer.index],
      submesh.indexBuffer
    ].forEach { buffer in
      encoder.useResource(buffer, usage: .read, stages: .vertex)
    }
    [
      model.modelParamsBuffer,
      submesh.materialBuffer
    ].forEach { buffer in
      encoder.useResource(buffer, usage: .read,
stages: .fragment)
    }
  }
  encoder.popDebugGroup()
}
```

Here, you ensure that all resources are definitely resident on the GPU. The code is longwinded, but the CPU overhead of running it is negligible. Ensuring that all resources are on the GPU means that you are less likely to run the risk of your computer locking up, or some other buffer corruption.

➤ Call this method in draw(commandBuffer:scene:uniforms:) after the guard where you create the render command encoder.

`useResources(encoder: renderEncoder, models: scene.models)`

<a id="page-668"></a>

## **5. Executing the Command List**

All the code you have written in this chapter has been building up to one command. Drum roll….

➤ Still in IndirectRenderPass.swift, add the following code to draw(commandBuffer:scene:uniforms:), before renderEncoder.endEncoding():

```
renderEncoder.executeCommandsInBuffer(
  icb, range: 0..<scene.models.count)
```

This code will execute all the commands in the indirect command buffer’s list within the range specified here. If you specify a range of 0..&lt;1, then only the first draw call would be performed.

➤ Build and run the app, and switch to Indirect encoding.

And… your app crashes:

```
The indirect command buffer inherits pipelines
( inheritPipelineState = YES) but the render pipeline set on
this encoder does not support indirect command buffers
( supportIndirectCommandBuffers = NO )
```

When you use a pipeline state in an indirect command list, you have to tell it that it should support indirect command buffers.

➤ Open Pipelines.swift, and add this to createForwardPSO(indirect:) before return:

`pipelineDescriptor.supportIndirectCommandBuffers = indirect`

In IndirectRenderPass.init(), you set up the pipeline state with indirect set to true.

<a id="page-669"></a>

➤ Build and run the app, and switch to Indirect encoding.

![Figure](Metal_by_Tutorials_v500mpdf/7e7de81df4e7da2446801782.png)

_Indirect encoding_

This may not be the most exciting result. Both forward rendering and indirect encoding renders look exactly the same. But behind the scenes, it’s a different story. Very little is happening in your render loop, and all the heavy lifting is done at the very start of the app. Success!

➤ Capture the GPU workload, and expand both the Indirect Command Encoding render pass and Indirect Command Encoding.

![Figure](Metal_by_Tutorials_v500mpdf/de3039cdf18b9c0c07ce0c96.png)

_Execute indirect commands_

<a id="page-670"></a>

➤ In the bound resources, double-click Indirect Command Buffer.

![Figure](Metal_by_Tutorials_v500mpdf/0850a550cb16d51326b0b1a8.png)

_The indirect command list_

You see both your draw call commands listed with their encoded resources.

As previous stated, in this app you won’t notice any improvement in performance. CPU indirect rendering is only worthwhile if you’re rendering thousands of static models. However, you now have the skills to approach GPU-driven rendering in the next chapter!

## **Key Points**

• Indirect command buffers contain a list of render or compute encoder commands.

• You can create the list of commands on the CPU at the start of your app. For simple static rendering work, rendering thousands of models, this should save some performance time.

<a id="page-671"></a>

# **Section IV: Pushing the GPU**

In this final section, you’ll learn how to get the most out of the GPU. You’ll encode commands on the GPU and learn a new pipeline with mesh shading. As a bonus, you’ll also do some post-processing with Metal Performance Shaders. To wrap up, you’ll consider how best to profile and optimize your game.

<a id="page-672"></a>

# 27

# Chapter 27: GPU Command Encoding

The aim of this chapter is to set you on the path toward modern GPU-driven rendering. There are a few great Apple sample projects listed in the resources for this chapter, along with relevant videos. However, the samples can be quite intimidating. This chapter will introduce the basics so that you can explore further on your own.

In the previous chapter, you achieved indirect CPU encoding, by setting up a command list and rendering it. You created a loop that executes serially on the CPU. This loop is one that you can easily parallelize.

Each ICB draw call command executes one after another, but by moving the command creation loop to the GPU, you can create each command at the same time over multiple GPU cores:

![Figure](Metal_by_Tutorials_v500mpdf/f9542df6c0e17991e3b4bf61.png)

_GPU command creation_

<a id="page-673"></a>

When you come to write real-world apps, setting up the render loop at the very start of the app is impractical. In each frame, you’ll be determining which models to render. Are the models in front of the camera? Is the model occluded by another model? Should you render a model with lower level of detail? By creating the command list every frame, you have complete flexibility in which models you should render, and which you should ignore.

As you’ll see, the GPU is amazingly fast at creating these render command lists, so you can include this process each frame.

## **The Starter Project**

➤ In Xcode, open the starter project, and build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/3c48131d3c609e36a549f11c.png)

_The starter app_

The starter project is almost the same as the final project from the previous chapter with these exceptions:

• The radio button options are both for indirect encoding, one on the GPU and one on the CPU.

• The two render passes are held in IndirectRenderPass.swift and GPURenderPass.swift. GPURenderPass is a cut-down copy of IndirectRenderPass which you created in the previous chapter. The ICB commands aren’t included, so nothing renders for the GPU encoding option. You’ll add the commands in a shader function that runs on the GPU.

• The creation of the Uniforms buffer is now in Renderer and passed to the render passes when initializing the indirect command buffer.

<a id="page-674"></a>

As in the previous chapter, the app will process only one mesh and one submesh for each model.

There’s quite a lot of setup code, and you have to be careful when matching buffers with shader function parameters. If you make an error, it’s difficult to debug it, and your computer may lock up. Running the app on an external device, such as iPhone or iPad is preferable, if slightly slower.

These are the steps you’ll take through this chapter:

1. Organize your scene data.

2. Add the scene data to one big buffer.

3. Create the compute shader function.

4. Create the compute pipeline state object.

5. Encode the ICB.

6. Set up the compute shader threads and arguments.

<a id="page-675"></a>

## **1. Organizing Your Scene**

Instead of handing the GPU one model at a time to encode, you’ll give a GPU compute shader function your whole scene organized into buffers. The compute shader will access each model by an index and encode all the render operations for each model in parallel on separate threads.

![Figure](Metal_by_Tutorials_v500mpdf/457232188e661455572062c0.png)

_Creating commands per thread_

<a id="page-676"></a>

For the models’ vertex buffers and materials, you’ll create argument buffers containing the GPU addresses for all the necessary model buffers. You’ll need to hold:

• Mesh data: the addresses of the vertex buffers and submesh indices. For simplicity, your app only processes one submesh. In a real app, you’d separate this out into mesh data and submesh data.

• Model data: the materials and transform data for each model.

This will make up the scene data, so, just for fun, you’ll have an extra step of indirection by having a scene argument buffer that points to the mesh and model data.

➤ In the Shaders folder, create a new header file called SceneData.h.

In this file, you’ll define the necessary structures for both Metal and Swift.

➤ Before `#endif`, add this code:

```
#if __METAL_VERSION__
// MARK: - Metal Shading Language

#include <metal_stdlib>
using namespace metal;

struct SceneData {
  constant float3* positionsAndNormals;
  constant float2* uvs;
  constant uint32_t* indices;
  uint32_t indexType;
  uint32_t indexCount;
  constant ShaderMaterial* materials;
  constant ModelParams* modelParams;
};

#else
// MARK: - Swift side

# endif
```

Here, you create the structures that you’ll need for accessing the argument buffers in Metal.

➤ After `// Mark: - Swift side`, add this code:

```
#include <Metal/Metal.h>

struct SceneData {
```

<a id="page-677"></a>

```
  uint64_t positions;
  uint64_t uvs;
  uint64_t indices;
  uint32_t indexType;
  uint32_t indexCount;
  uint64_t materials;
  uint64_t modelParams;
};
```

Here, you define the Swift resource argument buffers that point to the scene data. These match the Metal resources.

➤ Open **Common.h**, and after defining `ModelParams`, add this code:

`#import "SceneData.h"`

You need to add it after ModelParams, as SceneData requires knowledge of this structure.

## **2. Creating the Scene Data Buffer**

Your current model data structure looks like this:

![Figure](Metal_by_Tutorials_v500mpdf/dcd9b153163dc07856f89c9f.png)

_Model data hierarchy_

<a id="page-678"></a>

Ideally, you’d flatten your data into several buffers with this scene hierarchy:

![Figure](Metal_by_Tutorials_v500mpdf/09d8d05a27e5f9eb13d55d17.png)

_Scene data_

However, as you’re creating a less complex app with only one mesh and one submesh per model, you’ll flatten all your data into one sceneBuffer that holds all the data for all the models:

![Figure](Metal_by_Tutorials_v500mpdf/274f6646642682b68adf3fd7.png)

_Simplified scene data_

➤ Open GPURenderPass.swift in the Render Passes folder and add these new properties to GPURenderPass that you’ll use to hold your scene data:

```
var sceneBuffer: MTLBuffer!
var modelParamsBufferArray: [MTLBuffer] = []
```

You’ll initialize these buffers in initialize(models:). Notice that initializeICBCommands(\_:) differs from the previous chapter. It now only consists of setting up the indirect command buffer that the compute shader will fill.

<a id="page-679"></a>

➤ At the end of `initialize(models:)`, add this code:

```
let sceneBufferSize = MemoryLayout<SceneData>.stride *
models.count
sceneBuffer = Renderer.device.makeBuffer(length:
sceneBufferSize)!
sceneBuffer.label = "Scene Buffer"
var scenePtr = sceneBuffer.contents()
  .assumingMemoryBound(to: SceneData.self)
for model in models {
  let mesh = model.meshes[0]
  let submesh = mesh.submeshes[0]

  // add data to the scene buffer here

  // encode ModelParams

  scenePtr = scenePtr.advanced(by: 1)
}
```

You initialize the scene buffer with the correct size. You then set up a pointer binding the memory to SceneData so you can access the contents more easily.

Iterating through all the models, you’ll now add the data to the scene buffer.

➤ Replace `// add data to the scene buffer here` with this code:

```
scenePtr.pointee.positions = mesh.vertexBuffers[0].gpuAddress
scenePtr.pointee.uvs = mesh.vertexBuffers[1].gpuAddress
scenePtr.pointee.indices = submesh.indexBuffer.gpuAddress
scenePtr.pointee.indexType = submesh.indexType == .uint16 ? 0 :
1
scenePtr.pointee.indexCount = UInt32(submesh.indexCount)
scenePtr.pointee.materials = model.meshes[0].submeshes[0]
  .materialBuffer.gpuAddress
```

Each buffer resource has a GPU address. Apple Silicon has a unified memory architecture, where both CPU and GPU share the same physical memory. The advantage is that there is little transfer overhead.

The model’s vertex buffers and submesh data are the details that the GPU will need to render each model.

Adding the model’s transform and tiling data is a little more complex. You’ll still be using the vertex function vertex\_main and the fragment function fragment\_main to process the render. These functions expect a structure ModelParams. However, the compute shader can’t create a new buffer from a structure. You’ll need to transfer ModelParams to a buffer, and then add this buffer to the scene buffer.

<a id="page-680"></a>

➤ Replace `// encode ModelParams` with this code:

```
// 1
var modelParams = ModelParams(
  modelMatrix: model.transform.modelMatrix,
  tiling: model.tiling)
// 2
let modelParamsBufferSize = MemoryLayout<ModelParams>.stride
let modelParamsBuffer = Renderer.device.makeBuffer(
  bytes: &modelParams, length: modelParamsBufferSize)!
modelParamsBuffer.label = "Model Params"
// 3
scenePtr.pointee.modelParams = modelParamsBuffer.gpuAddress
// 4
modelParamsBufferArray.append(modelParamsBuffer)
```

Going through the code:

1. Fill out ModelParams with the data that the vertex and fragment functions expect.

2. Create an MTLBuffer from ModelParams.

3. Add the GPU address pointer to the ModelParams buffer to the scene buffer.

4. Retain the buffer in memory by adding it to modelParamsBufferArray. If you don’t do this, the app will release modelParamsBuffer as soon as it has finished using it in the for loop.

You’ve now made a massive scene buffer that you can transfer to the GPU with one binding.

## **3. Creating the Compute Shader Function**

Now you’ll create the indirect command buffer on the GPU. Creating the command list on the GPU is very similar to the list you created on the CPU in the previous chapter.

➤ In the Shaders folder, create a new Metal file named ICB.metal, and add the following:

```
#import "Common.h"

// 1
struct ICBContainer {
  command_buffer icb [[id(0)]];
};
```

<a id="page-681"></a>

```
kernel void encodeICB(
  // 2
  constant SceneData* scene [[buffer(0)]],
  constant Uniforms &uniforms [[buffer(UniformsBuffer)]],
  // 3
  device ICBContainer *icbContainer [[buffer(ICBBuffer)]],
  // 4
  uint modelIndex [[thread_position_in_grid]])
{
}
```

Going through the code:

1. You can only transfer an indirect command buffer to the GPU via an argument buffer. In GPURenderPass, you’ll encode icb into a container buffer shortly.

2. Here is the data for the scene. The compute function will extract each model’s data from scene and use it to fill out the draw command.

3. The indirect command buffer needs to be in the device space, as you’ll be writing to it in this function.

4. The compute function will process every model on its own thread, and the position in the grid will provide the index into scene.

Now that you’ve set up all the data, it’s an easy task to encode the draw call.

➤ Add this to encodeICB:

```
// 1
SceneData model = scene[modelIndex];
command_buffer icb = icbContainer->icb;

// 2
bool isVisible = true;
// 3
render_command cmd(icb, modelIndex);
if (isVisible) {
  cmd.set_vertex_buffer(&uniforms, UniformsBuffer);
  cmd.set_vertex_buffer(model.positionsAndNormals,
VertexBuffer);
  cmd.set_vertex_buffer(model.uvs, UVBuffer);
  cmd.set_vertex_buffer(model.modelParams, ModelParamsBuffer);
  cmd.set_fragment_buffer(model.materials, MaterialBuffer);
  cmd.set_fragment_buffer(model.modelParams, ModelParamsBuffer);
} else {
// 4
  cmd.reset();
}
```

<a id="page-682"></a>

Going through the code:

1. You retrieve the model and draw arguments using the thread position in grid.

2. isVisible is doing a lot of heavy lifting here. You may have wondered what you’re gaining from moving the encoding to the GPU. This is the place where you can decide whether or not to render the model. You can call a function to work out whether the model is behind the camera. If the model has multiple levels of detail, you could work out which one to render.

3. As you’re not doing any visibility testing here, you always create the render command and encode the operations just as you did in Swift.

4. If you don’t want to render this particular model, you tell the ICB to ignore this draw.

Finally, you’ll encode the draw call.

➤ Add this code before the else in encodeICB:

```
if (model.indexType == 0) {
  // uint16 indices
  cmd.draw_indexed_primitives(
    primitive_type::triangle,
    model.indexCount,
    (constant ushort*) model.indices,
    1);
} else {
  // uint32 indices
  cmd.draw_indexed_primitives(
    primitive_type::triangle,
    model.indexCount,
    (constant uint32_t*) model.indices,
    1);
}
```

Here, you create the draw call, testing which index type the model is using. In your app, the ground model uses uint32 indices and the house model uint16. It’s very important to get this data type right, otherwise the vertex function won’t be able to access the indices correctly, and you’ll get weird visual errors that are hard to debug.

<a id="page-683"></a>

![Figure](Metal_by_Tutorials_v500mpdf/debb040f0c510f3a98e66428.png)

_Incorrect indices_

You’ve now encoded a complete draw call, and that’s all that’s required for the compute function. Your next task is to set up the compute function on the CPU side, with a compute pipeline state and pass all the data to the compute function.

## **4. Creating the Compute Pipeline State Object**

➤ Open GPURenderPass.swift, and create these new properties in GPURenderPass:

```
let icbPipelineState: MTLComputePipelineState
let icbComputeFunction: MTLFunction
```

To run the compute function you just created, you’ll need a new compute pipeline state.

➤ Add the following code to the end of init():

```
icbComputeFunction =
  Renderer.library.makeFunction(name: "encodeICB")!
icbPipelineState = PipelineStates.createComputePSO(
  function: "encodeICB")
```

This code creates the compute function in the Metal library, and also the compute pipeline state.

<a id="page-684"></a>

## **5. Encoding the ICB**

The encodeICB compute function requires as input a buffer that contains the indirect command buffer.

➤ In `GPURenderPass`, add the container buffer:

`var icbContainer: MTLBuffer!`

➤ At the end of `initializeICBCommands(_:)`, add this code:

```
let icbEncoder = icbComputeFunction.makeArgumentEncoder(
  bufferIndex: ICBBuffer.index)
icbContainer = Renderer.device.makeBuffer(
  length: icbEncoder.encodedLength,
  options: [])
icbEncoder.setArgumentBuffer(icbContainer, offset: 0)
icbEncoder.setIndirectCommandBuffer(icb, index: 0)
```

You can’t send an indirect command buffer directly to the GPU, as it needs to be verified internally first as being suitable for the GPU. You create the argument encoder with reference to the compute function that will use it. So when you set the argument buffer as the container, together with the indirect command buffer, this verification can take place.

## **6. Setting up the Compute Command Encoder**

You’ve done all the preamble and setup code. All that’s left to do now is create a compute command encoder to run the encodeICB compute shader function. The function will create a render command to render every model.

➤ Still in GPURenderPass.swift, add a new method to GPURenderPass:

```
func encodeICB(
  commandBuffer: MTLCommandBuffer,
  models: [Model],
  uniforms: MTLBuffer
) {
  guard let computeEncoder =
    commandBuffer.makeComputeCommandEncoder() else { return }
  computeEncoder.label = "GPU Encoding"

  computeEncoder.setComputePipelineState(icbPipelineState)
  computeEncoder.setBuffer(sceneBuffer, offset: 0, index: 0)
  computeEncoder.setBuffer(
    uniforms, offset: 0, index: UniformsBuffer.index)
  computeEncoder.setBuffer(
```

<a id="page-685"></a>

```
    icbContainer, offset: 0, index: ICBBuffer.index)
}
```

Here, you create the compute command encoder and set the arguments that the compute function encodeICB will use.

➤ Add the following code to the end of encodeICB(commandBuffer:models:uniforms:):

```
// Dispatch threads
let threadExecutionWidth = icbPipelineState.threadExecutionWidth
let drawCount = models.count // should be number of draw calls
let threads = MTLSize(width: drawCount, height: 1, depth: 1)
let threadsPerThreadgroup = MTLSize(
  width: threadExecutionWidth, height: 1, depth: 1)
computeEncoder.dispatchThreads(
  threads, threadsPerThreadgroup: threadsPerThreadgroup)
computeEncoder.endEncoding()
```

Here, you decide on how many draw calls you need to create and dispatch the compute encoder with that many threads.

➤ Call this method at the top of draw(commandBuffer:scene:uniforms:):

```
encodeICB(
  commandBuffer: commandBuffer,
  models: scene.models,
  uniforms: uniforms)
```

Now you’re ready to run the app. You already set up the render command encoder in the previous chapter, and you can use the same execution command on the ICB. The only difference is that you filled the ICB on the GPU instead.

➤ Build and run the app, and your scene will appear.

![Figure](Metal_by_Tutorials_v500mpdf/2c490b8a0602add5aa176685.png)

_The rendered scene_

<a id="page-686"></a>

Because all your buffers are implicitly bound to the GPU, the GPU capture is unable to put together the scene, and you’ll get a blank render target there.

➤ Back in GPURenderPass.swift, add this code to the end of useResources(encoder:models:), before encoder.popDebugGroup:

```
encoder.useResource(sceneBuffer, usage: .read, stages: [.vertex,
.fragment])
modelParamsBufferArray.forEach {
  encoder.useResource($0, usage: .read, stages:
[.vertex, .fragment])
}
```

Note: even though useResource(\_:,usage:,stages:) is very efficient, and adds little to the run time load, you can work out which buffers are actually resident, and surround the others with #if DEBUG...endif. That way you’ll be able to view the GPU capture, and the commands won’t appear in the release version.

➤ Now, build and run the app, and capture the GPU frame. Take a look at the Command Buffer, the GPU Encoding Pass, and select dispatchThreads to see all the resources bound to the compute pass.

![Figure](Metal_by_Tutorials_v500mpdf/b4dac188404cad7f9ce10c0d.png)

_Compute pass bound resources_

<a id="page-687"></a>

➤ Double click Scene Buffer under Compute and check that your scene data is properly formatted.

![Figure](Metal_by_Tutorials_v500mpdf/c847608a75148704c98e71cc.png)

_Formatted scene data_

You should have two entries, one for each model. Each of the properties has an arrow indicating that it points to another buffer. You can click this arrow to view the contents of the other buffers.

The GPU Command Encoding render pass resources should be the same as the previous chapter.

As in the previous chapter, the app probably doesn’t show much speed improvement. In fact, with the overhead of creating the commands, the efficiency may actually have deteriorated. The real power of GPU-driven rendering is in dynamic culling and level of detail. When you combine the technique of creating a command list on the GPU with other techniques such as mesh shading, you’ll realize the full power of the GPU. The next chapter will introduce you to the mesh shading pipeline.

## **Key Points**

• You can create commands in indirect command buffers on either the CPU or the GPU.

• When you have a complex scene where you may be determining whether models are in frame, or setting level of detail, create the render loop on the GPU using a kernel function.

• You can use argument buffers to create large blocks of memory containing an entire scene. Use the GPU address of buffers, held in unified memory, as pointers in the argument buffer.

<a id="page-688"></a>

## **Where to Go From Here?**

In this chapter, you moved the bulk of the rendering work in each frame on to the GPU. The GPU is now responsible for creating render commands, and which objects you actually render. Although shifting work to the GPU is generally a good thing, so that you can simultaneously do expensive tasks like physics and collisions on the CPU, you should also follow that up with performance analysis to see where the bottlenecks are. You can read more about this in Chapter 30, “Profiling”.

GPU-driven rendering is a fairly recent concept, and the best resources are Apple’s WWDC sessions listed in references.markdown in the resources folder for this chapter.

![Figure](Metal_by_Tutorials_v500mpdf/39c6862078b2b9bb72e11242.png)

_Apple sample: Modern Rendering With Metal_

Apple’s sample: Modern Rendering with Metal (https://developer.apple.com/ documentation/metal/metal\_sample\_code\_library/modern\_rendering\_with\_metal) renders Amazon’s huge Bistro scene, with heavy mesh resources and many lights. The sample uses several advanced techniques including indirect command buffers for GPU-driven rendering, and is the best project to tear apart and analyze.

<a id="page-689"></a>

# 28

## Chapter 28: Geometry Creation with Mesh Shaders

Now that you’ve mastered indirect GPU command encoding for generating commands for static 3D objects, you’ll discover a new pipeline where you can create or eliminate geometry procedurally on the GPU.

Grass is an ideal example. Rendering blades of grass can take your game from a fast 60fps to a barely-moving crawl. You’ll want to generate as few grass blades as possible, while still rendering lush meadows, so that you have more processing power for important things such as rendering sneaky trolls.

## **The Mesh Shader Pipeline**

While the traditional vertex shader render pipeline is still good for standard 3D rendering, the newer mesh shader pipeline allows more fine-grained procedural geometry creation and geometry culling.

Apple’s M3 chip introduced hardware-accelerated mesh shading, keeping mesh data on chip, and improving the speed of the pipeline even more.

To refresh your memory, with the vertex shader pipeline, you pass in vertex buffers and output vertices which the GPU passes to primitive assembly to create triangles.

<a id="page-690"></a>

Blue indicates programmable functions, and pink indicates fixed GPU functions:

![Figure](Metal_by_Tutorials_v500mpdf/dc8f6cf4fe26d4a3ddef46c2.png)

_The vertex shader pipeline_

The rasterizer takes the triangles output from the vertex function and passes fragments to the fragment shader. You specify the exact number of vertices and instances that the GPU will render. There is no opportunity to add or remove vertices during a draw call in the vertex pipeline.

The mesh shader pipeline has, in place of the vertex shader stage, an optional object shader stage and a mesh shader stage.

![Figure](Metal_by_Tutorials_v500mpdf/149c0afe7c33bb4ab5907cd6.png)

_The mesh shader pipeline_

You can pass in any data to the object function, such as camera data, scene data or textures. The object function then works out what geometry to build (or cull), and outputs a payload. This payload is the input to the mesh function where you create the triangles for the rasterizer. From there, the pipeline is the same as the vertex pipeline.

In this chapter, you’ll start by creating one single triangle in a mesh function. After that, you’ll generate grass blades in a tiled grid. This is where mesh shading shines. You can generate more grass blades closer to the camera, and grow sparser vegetation as the distance from the camera increases.

<a id="page-691"></a>

## **The Starter Project**

The starter project for this chapter simply renders a triangle with three vertices using the standard vertex shader pipeline. There are three user options that load different render passes:

• Vertex Shader: This runs the standard vertex render pass.

• Mesh Shader: You’ll set up this render pass to render a triangle using the mesh shader pipeline.

• Grass Shader: After you’ve achieved writing one triangle using a mesh shader, you’ll generate many of them and render some lush stylized grass.

➤ Build and run the app, and you’ll see that Vertex Shader draws a triangle, and the other two options run minimal render passes, producing a clear background.

![Figure](Metal_by_Tutorials_v500mpdf/3ab56f4a63b4efc522995c11.png)

_The starter project_

➤ Examine the project, which contains nothing that you haven’t covered before.

## **Render a Triangle With a Mesh Shader**

Rendering a triangle using a mesh shader is quite similar to using a compute shader. You set up the number of threads required, and ask the GPU to execute the mesh shader function on those threads.

You’ll first set up the Swift side, and then set up a mesh shader function. You won’t need an object function as there’s no conditional generation or culling here. You’ll simply render the same three vertices over and over.

<a id="page-692"></a>

## **The Mesh Shader Render Pass**

➤ In the Render Passes folder, open MeshRenderPass.swift.

MeshRenderPass is currently an outline render pass which sets up a basic render command encoder with no draw commands.

As you’ll call a special shader function, you’ll need a different pipeline state. In draw(commandBuffer:scene:uniforms:), instead of setting the triangle buffer, as you would for the vertex pipeline, you’ll set up the threads needed to run a mesh shader function.

➤ Open Pipelines.swift, and create a new method in PipelineStates:

```
static func createMeshPSO()
  -> MTLRenderPipelineState {
  // 1
  let objectFunction: MTLFunction? = nil
  let meshFunction = Renderer.library.makeFunction(name:
"mesh_main")
  let fragmentFunction =
    Renderer.library.makeFunction(name: "fragment_main")
  // 2
  let pipelineDescriptor = MTLMeshRenderPipelineDescriptor()
  pipelineDescriptor.objectFunction = objectFunction
  pipelineDescriptor.meshFunction = meshFunction
  pipelineDescriptor.fragmentFunction = fragmentFunction
  pipelineDescriptor.colorAttachments[0].pixelFormat
    = Renderer.viewColorPixelFormat
  pipelineDescriptor.depthAttachmentPixelFormat = .depth32Float
  // 3
  let meshPSO: MTLRenderPipelineState
  do {
    (meshPSO, _) = try Renderer.device.makeRenderPipelineState(
    descriptor: pipelineDescriptor, options: [])
  } catch {
    fatalError("Mesh PSO not created \
(error.localizedDescription)")
  }
  return meshPSO
}
```

Even though the plan is to use the mesh shading pipeline, you’ll still create an MTLRenderPipelineState. This method is very similar to createVertexPSO(), with the following differences:

1. For this simple triangle, you won’t create an object function. You create a meshFunction instead of a vertexFunction. You can still use the same fragment function, as that part of the pipeline doesn’t change.

<a id="page-693"></a>

2. You create a mesh render pipeline descriptor which has a few different options.

3. The mesh render pipeline state has a different “make” method, so you create the pipeline state object here, instead of calling createPSO(descriptor:). makeRenderPipelineState(descriptor:options:) returns both the new pipeline state object and a reflection instance containing information about the function arguments.

➤ In **MeshRenderPass.swift**, in `init()`, change the pipeline state assignment to:

`pipelineState = PipelineStates.createMeshPSO()`

Now the GPU will use the mesh shader pipeline.

When setting up the required threads, the GPU needs to know these three things:

1. How many thread groups to process. Each thread group will run one object function and one mesh function. Taking grass as an example, which you’ll revisit later, you’ll process tiles of grass blades spread across the landscape. If you have 10 x 10 tiles, you’ll process an object grid of 10 x 10 thread groups. Each object thread group will spawn a mesh grid to process the blades of grass.

2. How many threads per object thread group. When you calculate grass blades in a tile it’s simple enough that one thread will handle it.

3. The number of threads per mesh threadgroup. This will be greater than or equal to the number of vertices that make up your grass blade.

➤ In MeshRenderPass.draw(commandBuffer:scene:uniforms:), replace // add code here with:

```
// 1
let threadgroupsPerGrid =
  MTLSize(width: 1, height: 1, depth: 1)
// 2
let threadsPerObjectThreadgroup =
  MTLSize(width: 1, height: 1, depth: 1)
// 3
let threadsPerMeshThreadgroup =
  MTLSize(width: 3, height: 1, depth: 1)
```

Going through the thread requirements:

1. You’ll render one triangle.

2. You won’t be creating an object function, and you don’t need to run extra threads here. The compiler requires that you add a size here though.

<a id="page-694"></a>

3. You’ll output three vertices for the triangle.

➤ Continue, adding this code:

```
renderEncoder.drawMeshThreadgroups(
  threadgroupsPerGrid,
  threadsPerObjectThreadgroup: threadsPerObjectThreadgroup,
  threadsPerMeshThreadgroup: threadsPerMeshThreadgroup)
```

You set the draw command on the render command encoder. And that’s all that’s needed to launch a simple mesh shader pipeline.

## **The Mesh Shader**

➤ In the Shaders folder, open Shaders.metal.

This file contains your vertex and fragment functions. You’ll add the mesh function here, formatting the data so that it returns VertexOut, suitable for the rasterizer and fragment function. VertexOut is defined in ShaderDefs.h.

In most cases, you would first create an object shader function which inputs a payload to the mesh function. However, you don’t need that here.

➤ At the end of the file, define the mesh shader output structure:

```
using MeshTriangle = metal::mesh<
  VertexOut, void, 3, 1,
  metal::topology::triangle>;
```

metal::mesh&lt;V, P, NV, NP, t&gt; is a struct type that represents the data that the mesh function will output.

• V: The vertex type. You’ll create a VertexOut structure for each vertex.

• P: The primitive type. This is a user defined structure that describes the payload from the object function. In this case, you don’t have one.

• NV: The maximum number of vertices output from each thread group. There is a hard Metal maximum of 256 vertices.

• NP: The maximum number of primitives output. Here, the primitive is a triangle, but it could be points or lines too. The hard maximum is 512 primitives.

• t: The topology of the mesh. Here, the topology is a triangle.

<a id="page-695"></a>

➤ Create the mesh shader header:

```
[[mesh]] void mesh_main(
    MeshTriangle triangle,
    uint threadID[[thread_index_in_threadgroup]])
{
}
```

You mark the function with the [[mesh]] attribute and declare the MeshTriangle output. threadID will give you the thread ID, which will be in the range 0 to 2 for each of the vertices.

➤ In `mesh_main`, create some hard-coded values:

```
float4 positions[3] = {
    float4( 0.0,  0.5, 0.0, 1),
    float4(-0.5, -0.5, 0.0, 1),
    float4( 0.5, -0.5, 0.0, 1)
};

float4 colors[3] = {
    float4(1.0, 0.0, 0.0, 1.0),
    float4(0.0, 1.0, 0.0, 1.0),
    float4(0.0, 0.0, 1.0, 1.0)
};
```

Here, you set up the vertex positions and vertex colors.

➤ Continue, adding this code:

```
// 1
if (threadID < 3) {
  // 2
  triangle.set_vertex(threadID, VertexOut {
    .position = positions[threadID],
    .color = colors[threadID]
  });
  // 3
  triangle.set_index(threadID, threadID);
}
```

Going through this code:

1. Only threads 0, 1 and 2 will write vertices.

2. Write the VertexOut data for each vertex.

<a id="page-696"></a>

3. Write the index buffer for the vertex. The first threadID is the index number, and the second threadID is the vertex number. So each thread sets the index and vertex:

thread 0: index 0: vertex: 0 thread 1: index 1: vertex: 1 thread 2: index 2: vertex: 2

➤ Add this code to the end of mesh\_main:

```
if (threadID == 0) {
  triangle.set_primitive_count(1);
}
```

On the first thread only, you output how many primitives you will output to the rasterizer. In this case, only one triangle.

Now that you’ve set up the render pass and the mesh shader function you’re all ready to go.

➤ Build and run the app and choose the option Mesh Shader.

![Figure](Metal_by_Tutorials_v500mpdf/60544c68fcbd0a70186c2e02.png)

_Mesh shader output_

In the mesh function, you set up each vertex to have a different color, so instead of the plain orange set up by the vertex function, you have a brilliant multicolored triangle.

<a id="page-697"></a>

## **Procedural Grass Generation**

Now that you know how to render one triangle, the next step is to procedurally generate many triangles for grass.

Prior to mesh shading, you could set up your geometry creation or buffers of culled geometry in compute shaders. This means that you’d have to switch command encoders from the compute encoder to the render encoder, and rebind all GPU resources. Any buffers created between the two encoders would swap out to device memory.

Mesh shaders let you create or cull geometry, and then render it, all in the same render command encoder. You’ll now explore the process while generating grass blades in a tiled grid:

![Figure](Metal_by_Tutorials_v500mpdf/f3d5400d91a88bcaee3a6ffe.png)

_Rendering grass_

As tiles recede from the camera, you’ll render fewer grass blades on them. In addition, if a tile is behind the camera, it won’t render anything.

This will involve culling tiles, and deciding how many grass blades are on each tile.

<a id="page-698"></a>

• Object stage: You’ll input tile and camera data to the object shader. The object shader function will run for each tile, and calculate the distance of the tile from the camera. Using that distance the function decides on the level of detail (LOD). The object function will then output as payload the positions and count of the grass blades in the tile.

• Mesh stage: The GPU will launch one mesh threadgroup for each grass blade in each tile. Each threadgroup runs multiple threads, with the first three threads creating the three vertices, forming, in this example, one primitive triangle. This triangle will then proceed to the rasterizer and fragment shader as usual. Instead of one triangle, the object shader could pass on LOD, and the mesh function generate more detailed hero grass closer to the camera.

![Figure](Metal_by_Tutorials_v500mpdf/1764460dfdb783368e8b4aca.png)

_Object to mesh threadgroups_

Here’s how you’ll proceed:

1. Set up the mesh shader pipeline state, defining the shader functions.

2. Create a grass structure that defines how many tiles the terrain contains, and the density of grass within each tile.

3. Describe the draw call where you’ll bind the data to the render command encoder and calculate the number of threads and threadgroups needed.

4. Implement the object shader function to perform culling and determine the number of blades of grass (LOD) in each tile.

5. Implement the mesh shader function, generating vertices and output vertex positions to the rasterizer.

<a id="page-699"></a>

## **1. Set up the Pipeline State Object**

➤ In the Render Passes folder, open GrassRenderPass.swift and check out the code.

Again, this is a minimal render pass with the render command encoder set up with the pipeline state and depth/stencil state. First, you’ll need to set up the shader functions in a new pipeline state object.

➤ Open Pipelines.swift and copy createMeshPSO() to a new method called createGrassPSO().

➤ Change the object stage function assignment at the top of createGrassPSO():

```
let objectFunction =
  Renderer.library.makeFunction(name: "object_grass")
```

➤ Change the mesh function to: &quot;mesh\_grass&quot;.

You’ll still use the same fragment function to render the triangle grass.

Open GrassRenderPass.swift, and change the pipeline state assignment in init() to call your new method:

`pipelineState = PipelineStates.createGrassPSO()`

## **2. Set up the Grass Input Data**

➤ In the Shaders folder, open Common.h, and add these new structures before #endif /\* Common\_h \*/:

```
#define MaxBladesPerTile 8

typedef struct {
  float maxDistance;
  float bladeVertices;
  float gridSize;
  float tileSize;
} GrassSettings;

typedef struct {
  matrix_float4x4 viewProjectionMatrix;
  simd_float3 cameraPosition;
  simd_float3 cameraForward;
} GrassUniforms;

typedef struct {
```

<a id="page-700"></a>

```
  simd_float3 bladePositions[MaxBladesPerTile];
  uint32_t bladeCount;
  simd_uint3 tileID;
} GrassPayload;
```

MaxBladesPerTile defines the number of grass blades on each tile. This needs to be within practical limits. There’s a hardware limit for the number of mesh threadgroups per object threadgroup of 1024. However, if you have 15x15 (225) tiles and render 100 blades per tile, you’d be launching at least 720,000 threads. Theoretically the GPU can cope with this, but you might be spending a large portion of your frame-time allowance on grass rendering.

You set MaxBladesPerTile to a low 8 blades per tile for the moment. It’s a constant, because you define the array of grass blade positions in GrassPayload using this size.

GrassSettings, which you’ll use in the object stage, contains the configuration of the grass terrain, such as size and density. You’ll update GrassUniforms on each frame and pass to both mesh and object stages. The object stage will create and output GrassPayload, which contains a fixed array of the positions and the number of grass blades to be generated.

➤ Open GrassRenderPass.swift, and add a new property to GrassRenderPass:

```
let grassSettings = GrassSettings(
  maxDistance: 15,
  bladeVertices: 3,
  gridSize: 3,
  tileSize: 3)
```

These are the settings:

• maxDistance: Any tile with a distance from the camera greater than maxDistance won’t render any grass.

• bladeVertices: This controls the number of threads in each mesh threadgroup. There’s a hard GPU maximum of 1024, but you’ll only generate one triangle for each blade.

• gridSize: Number of tiles per side. Here you’ll have a 3x3 grid with 9 tiles.

• tileSize: The world width and depth dimensions for each tile.

These are low numbers until the app is working. You’ll increase the values later.

<a id="page-701"></a>

## **3. The Draw**

➤ In draw(commandBuffer:scene:uniforms:), replace // add code here, and bind the data to the object stage:

```
var grassUniforms = GrassUniforms()
let viewProjectionMatrix =
  scene.camera.projectionMatrix * scene.camera.viewMatrix
grassUniforms.viewProjectionMatrix = viewProjectionMatrix
grassUniforms.cameraPosition = scene.camera.position
grassUniforms.cameraForward = scene.camera.forwardVector
renderEncoder.setObjectBytes(
  &grassUniforms,
  length: MemoryLayout<GrassUniforms>.stride,
  index: GrassUniformsBuffer.index)

renderEncoder.setMeshBytes(
  &grassUniforms,
  length: MemoryLayout<GrassUniforms>.stride,
  index: GrassUniformsBuffer.index)

var grassSettings = grassSettings
renderEncoder.setObjectBytes(
  &grassSettings,
  length: MemoryLayout<GrassSettings>.stride,
  index: GrassSettingsBuffer.index)
```

You set up the camera data for the frame and pass it to both object and mesh functions. In addition, the object function gets the grass settings where you’ll determine the size of the world and number of blades of grass per tile.

That’s the object and mesh stages set up. Now you’ll set up the thread details.

➤ Add this code after the previous code:

```
// 1
let threadgroupsPerGrid = MTLSize(
  width: Int(grassSettings.gridSize),
  height: 1,
  depth: Int(grassSettings.gridSize))
// 2
let threadsPerTile =
  MTLSize(width: 1, height: 1, depth: 1)
// 3
let threadsPerBlade = MTLSize(
  width: Int(grassSettings.bladeVertices),
  height: 1,
  depth: 1)
```

<a id="page-702"></a>

You set up the thread and threadgroup counts:

1. The grid size is your 2D 3x3 grid of tiles. There will be a total of 9 threadgroups.

2. You’ll only need one thread to perform each grid’s blade position and density calculations.

3. You configure the GPU to allocate three threads, one for each vertex to be created. You’ll initially just create a triangle for each blade of grass, but later on, if you decide to improve on the stylized grass, you can make your grass blade more realistic with more vertices.

➤ Add the draw call:

```
renderEncoder.drawMeshThreadgroups(
  threadgroupsPerGrid,
  threadsPerObjectThreadgroup: threadsPerTile,
  threadsPerMeshThreadgroup: threadsPerBlade)
```

You’ve completed the Swift setup. Now you’ll write the object and mesh shader functions.

## **4. The Object Shader Function**

➤ Create a new file in the Shaders folder, using the Metal File template, named GrassShaders.metal.

The GPU performs the object function on each tile. In the function, you’ll:

1. Calculate the world position of the tile.

2. Cull any tiles behind the camera.

3. Work out how many blades of grass to add to the tile, based on the distance from the camera.

4. Generate the position of each blade of grass in the tile. The positions and count are the object function’s payload.

5. Specify the number of mesh threadgroups to dispatch.

➤ Define the object function with this code:

```
#import "Common.h"
#import "ShaderDefs.h"

[[object]]
```

<a id="page-703"></a>

```
void object_grass(
  uint3 objectID [[threadgroup_position_in_grid]],
  constant GrassUniforms& uniforms
[[buffer(GrassUniformsBuffer)]],
  constant GrassSettings& settings
[[buffer(GrassSettingsBuffer)]],
  object_data GrassPayload& payload [[payload]],
  mesh_grid_properties meshGridProperties)
{
}
```

You define the object function with the `[[object]]` attribute.

Going through the parameters:

• objectID: The tile ID in the grid.

• uniforms and settings: These contain the grid and grass data.

• payload: The GPU allocates space in the object\_data address space for the payload data.

• mesh\_grid\_properties: You’ll set this at the end of the object function, to determine how many mesh threadgroups to spawn. This will be the number of blades generated per tile.

Before going any further, notice that you’re asking the GPU to allocate a certain amount of space for the payload. You tell the GPU how much space when you assign the pipeline state.

Open Pipelines.swift, and add this code to createGrassPSO() before creating meshPSO:

```
pipelineDescriptor.payloadMemoryLength =
  MemoryLayout<GrassPayload>.stride
```

Now the GPU will know how much space to allocate the payload. You didn’t have to do this in createMeshPSO(), because you didn’t create any payload from an object function.

➤ Back in **GrassShaders.metal**, add this code to the object function:

```
float halfGrid = (settings.gridSize - 1.0) * 0.5;
float3 tileCenter = float3(
  (float(objectID.x) - halfGrid) * settings.tileSize,
  0.0,
  (float(objectID.z) - halfGrid) * settings.tileSize
);
```

<a id="page-704"></a>

Here, you use the grid size and the object ID to calculate the world position of the tile.

➤ You don’t want to render any tiles that are behind the camera, so add this code:

```
float3 cameraToTile = normalize(tileCenter -
uniforms.cameraPosition);
float3 cameraForward = normalize(uniforms.cameraForward);
if (dot(cameraForward, cameraToTile) < -0.4) {
  meshGridProperties.set_threadgroups_per_grid(0);
  return;
}
```

You use the dot product to find the direction of the tile center from the camera and if the tile is behind the camera, you set the mesh threadgroups to zero and return from the function without rendering anything. You can’t do this in a vertex function!

➤ Continue, adding this code:

```
float distanceToCamera =
  length(uniforms.cameraPosition - tileCenter);
uint bladesInTile;
if (distanceToCamera < settings.maxDistance * 0.3) {
  bladesInTile = MaxBladesPerTile;
} else if (distanceToCamera < settings.maxDistance * 0.6) {
  bladesInTile = MaxBladesPerTile / 2;
} else if (distanceToCamera < settings.maxDistance) {
  bladesInTile = MaxBladesPerTile / 4;
} else {
  bladesInTile = 0;
}
if (bladesInTile == 0) {
  meshGridProperties.set_threadgroups_per_grid(0);
  return;
}
```

You calculate the distance of the tile from the camera. Based on that distance, you work out the number of blades of grass for this tile. If the distance is greater than the one you specified in GrassRenderPass, there will be no grass, so don’t render anything.

When you’ve completed your grass, you can experiment with the multipliers and divisors. You don’t want your grass “popping” when changing level of detail, but you want the lowest level of detail possible.

➤ Fill out the payload with this code:

`payload.bladeCount = bladesInTile;`

<a id="page-705"></a>

```
for (uint i = 0; i < bladesInTile; i++) {
    float t = float(i) / float(bladesInTile - 1);
    float x = (t - 0.5) * settings.tileSize * 0.5;
    payload.bladePositions[i] = tileCenter + float3(x, 0.0,
0.0);
}

payload.tileID = objectID;
```

For simplicity, you’ll create a single row of grass per tile. This should be a randomized distribution, but you’ll be able to visualize what’s happening more clearly if you can see the pattern.

➤ Lastly, spawn the mesh threadgroups per blade of grass by adding this code:

```
meshGridProperties.set_threadgroups_per_grid(
  uint3(bladesInTile, 1, 1));
```

## **5. The Mesh Shader Function**

With the object shader function outputting a payload of grass blades, you can create the mesh shader.

➤ Add the mesh shader function after the previous object function:

```
using GrassMesh = metal::mesh<VertexOut, void, 3, 1,
topology::triangle>;

[[mesh]]
void mesh_grass(
  uint meshID [[threadgroup_position_in_grid]],
  uint threadID [[thread_index_in_threadgroup]],
  const object_data GrassPayload& payload [[payload]],
  GrassMesh outputMesh,
  constant GrassUniforms& uniforms
[[buffer(GrassUniformsBuffer)]])
{
}
```

First, you define the structure for the output of the function using metal::mesh. VertexOut is the same structure that you used for the vertex and the other mesh function, which is defined in ShaderDefs.h.

You then define the mesh function with the [[mesh]] attribute. The mesh function will operate on every blade of grass output from the object function.

<a id="page-706"></a>

Going through the parameters:

• meshID: The blade index in the tile. Each mesh threadgroup will create the vertices for one blade.

• threadID: Using the thread ID within the mesh threadgroup, you’ll create one vertex.

• payload: This is the payload output by the object function.

• outputMesh: GrassMesh defines the data output by the mesh function. You’ll populate VertexOut for each vertex.

• uniforms: This contains the view data so that you can position the blade properly in the world. You’d usually position a vertex in the vertex function, but in the mesh pipeline, the mesh function takes its place.

➤ Add this code to `mesh_grass` to define the color and position for each vertex:

```
float4 position;
float4 color = { 0, 0.5, 0, 1 };
switch (threadID) {
  case 0:   // top vertex
    position = { 0, 1, 0, 1 };
    color = { 0.5, 0.8, 0, 1};
    break;
  case 1:   // bottom left vertex
    position = { -0.2, 0, 0, 1 };
    break;
  case 2:   // bottom right vertex
    position = { 0.2, 0, 0, 1 };
    break;
}
```

The lower vertices will have a dark green, and the top vertex will have a lime green color.

➤ Add this code to the end of mesh\_grass:

```
position += float4(payload.bladePositions[meshID], 0);
if (threadID < 3) {
  outputMesh.set_vertex(threadID, VertexOut {
    .position = uniforms.viewProjectionMatrix * position,
    .color = color
  });

  outputMesh.set_index(threadID, threadID);
}
if (threadID == 0) {
```

<a id="page-707"></a>

```
  outputMesh.set_primitive_count(1);
}
```

Here, you add the blade position, calculated in the object function, to the vertex position. When assigning the final position, you multiply by the view projection matrix, and the rest of the function is the same as the previous mesh function’s triangle.

➤ Build and run, select Grass Shader, and see your grassy meadow begin to take shape.

![Figure](Metal_by_Tutorials_v500mpdf/99b502b63fcc1a704b7cb742.png)

_First grass render_

The camera is positioned slightly back in the scene so that you can immediately see your 3x3 grid. The closest of the tiles has MaxBladesPerTile (8). As the tiles recede into the distance, the number halves to four. The furthest corners of the grid only contain two blades in each tile.

➤ Press WASD to move around the scene and the arrow keys to rotate. The number of blades will increase and decrease as you move.

➤ Press the 1 key above the alpha keys to view the scene from above. As you use WASD to move around, you can see the tiles being culled behind the camera.

![Figure](Metal_by_Tutorials_v500mpdf/12746f2ee5210d5116317279.png)

_Culled tiles_

<a id="page-708"></a>

The absence of tiles will be more obvious when you render more of them shortly.

Conceptually, that’s all there is to grass. You can, of course, enhance the placement and appearance.

## **Creating Randomness**

The grass is standing around like soldiers in a row. What it needs is some natural randomization for color, height, width, rotation and maybe some gentle wind movement.

Metal Shading Language doesn’t have a random function, so for positioning the grass, you’ll create a simple hash function that produces a number between [0, 1]. The function will use a hash technique that converts spatial coordinates into numbers that look random. The numbers generated are not truly random because the same input produces the same output. But that’s good, because your grass blades won’t suddenly change position.

➤ At the top of GrassShaders.metal, add the following code just above object\_grass:

```
float simpleHash(float2 coords) {
  float h = dot(coords, float2(127.1, 311.7));
  return fract(sin(h) * 43758.5453);
}
```

This is a common hash pattern used in shader programming. The magic numbers produce good distribution, and fract returns a number between [0, 1].

➤ In object\_grass, replace the for (uint i = 0; i &lt; bladesInTile; i++) loop with this code:

```
for (uint i = 0; i < bladesInTile; i++) {
  float randX = simpleHash(float2(objectID.xz) + float2(i, 0));
  float randY = simpleHash(float2(objectID.xz) + float2(0, i));
  float offsetX = (randX - 0.5) * settings.tileSize;
  float offsetZ = (randY - 0.5) * settings.tileSize;
  float3 offset = float3(offsetX, 0, offsetZ);
  payload.bladePositions[i] = tileCenter + offset;
}
```

Here, you use the random number function to position each blade.

<a id="page-709"></a>

➤ Build and run, and change the option to Grass Shader.

![Figure](Metal_by_Tutorials_v500mpdf/eca9366859b0d15d888392ae.png)

_Scattered grass_

Your grass is now scattered, but rather sparse. You can experiment with different settings, such as these:

➤ In Common.h, change MaxBladesPerTile to 512.

➤ In **GrassRenderPass.swift**, change `grassSettings` to:

```
let grassSettings = GrassSettings(
  maxDistance: 30,
  bladeVertices: 3,
  gridSize: 25,
  tileSize: 3)
```

You set the distance that the levels of detail will come into effect to be further, and you’ll have 625 tiles of grass. With these settings, iPad Air M3, which has hardware-accelerated mesh shading, takes 1.6ms per frame. iPad Mini 6, which has the older chip, takes 9.6ms per frame.

➤ Build and run, and change the option to Grass Shader.

![Figure](Metal_by_Tutorials_v500mpdf/9c72811c1468b298f71aa210.png)

_Lush grass_

That’s more like it! Do the challenge to improve your vegetation even further.

<a id="page-710"></a>

In this chapter, you rendered simple grass. However, mesh shaders are incredibly versatile. They excel anywhere that you want to generate geometry, such as hair or fur or grass, or using billboards for trees or crowds.

## **Meshlet Culling**

An important use case for mesh shaders is rendering levels of detail. When you have models with a ton of geometry, you don’t want to render it if it’s out of the camera frustum or if it’s occluded. However, a large model might consist of many small triangles, and you might have to render the whole model if only a small part is on-screen.

This is where meshlets come in to their own. You can divide your model’s triangles into groups of meshlets consisting of around 64 to 256 vertices each. When generating each meshlet, you can work out its bounding box and average face direction. An object shader function can then decide on the level of detail for that meshlet, reducing the number of vertices or eliminating them altogether as necessary.

You can read about this feature in Warren Moore’s comprehensive article: Mesh Shaders and Meshlet Culling in Metal 3 (https://metalbyexample.com/mesh-shaders/). The following image shows the Stanford Dragon split into colored meshlets, rendered using Warren’s sample code:

![Figure](Metal_by_Tutorials_v500mpdf/bddeb2e9ade52e3371f859a0.png)

_Stanford Dragon showing colored meshlets_

<a id="page-711"></a>

## **Challenge**

For your challenge, you’ll make the grass look more grassy and less triangular.

In the mesh shader function, use `simpleHash()` to randomize:

• The height of the blade.

• The color variation.

• The rotation.

You can use a range function for random variation offsets:

```
float randomRange(
  float2 coords,
  float offset,
  float minValue,
  float maxValue) {
  return simpleHash(coords + offset)
    * (maxValue - minValue) + minValue;
}
```

Where `coords` is the blade position and `offset` is an extra randomness.

The challenge project supplied for this chapter makes the grass blade narrower, and has an extra billboard rotation, so that the grass blades are always facing the camera.

![Figure](Metal_by_Tutorials_v500mpdf/b901e4e06185c36523ac0c11.png)

_Completed grass_

<a id="page-712"></a>

## **Key Points**

• Use the standard vertex pipeline for most rendering. You can use GPU indirect command encoding for camera frustum culling. Mesh shaders are useful for generating and culling simple geometry.

• There are two stages in the mesh shader pipeline. Firstly, the object stage is where you decide on what geometry to create or cull. Secondly, the mesh stage is where you create actual vertices.

• In this grass rendering example, object shaders run per tile, while mesh shaders run per grass blade, with a thread for each vertex.

• Metal Shading Language doesn’t provide a random number function. There are many different kinds of random number algorithms. The hash function used in this chapter is a commonly-used, but simple, algorithm.

## **Where to Go From Here?**

The grass you created in this chapter is highly stylized. For more natural grass, you’ll create more vertices than just a triangle. Wind blowing across the surface will enhance the effect enormously.

In the references.markdown file in the resources folder for this chapter, you’ll find some additional reading.

<a id="page-713"></a>

# 29

# Chapter 29: Metal Performance Shaders

In Chapter 19, “Tessellation &amp; Terrains”, you had a brief taste of using the Metal Performance Shaders (MPS) framework. MPS consists of low-level, fine-tuned, high-performance kernels that run off the shelf with minimal configuration. In this chapter, you’ll dive a bit deeper into the world of MPS.

Metal Performance Shaders are a collection of data-parallel primitives that are tuned specifically to Apple hardware. There are several different operation types:

• Image filters, such as convolutions and histograms.

• Neural networks for machine learning.

• Mathematical operations for solving systems of equations.

Think of MPS kernels as convenient black boxes that work efficiently and seamlessly with your command buffer. Simply give it the desired effect, a source and destination resource (buffer or texture), and then encode GPU commands on the fly!

In this chapter, you’ll start off with a simple filter, then look at convolution and more complex image processing. You’ll then get a taste of matrix and vector math using MPS.

<a id="page-714"></a>

## **The Sobel Filter**

The Sobel filter is a great way to detect edges in an image.

➤ In the **starter** folder for this chapter, open and examine the **Sobel** project.

Sobel is very simple having only a basic renderer set up in Renderer.swift. The asset catalog contains an image called “fruit”. Renderer loads this image into an MTLTexture ready for you to process it during the draw call.

![Figure](Metal_by_Tutorials_v500mpdf/7ee3b8d184d9840418e39b82.png)

_The fruit image_

If you run the app, you’ll probably get a pink view, as the renderer doesn’t render anything.

➤ In `draw(in:)`, replace `// add code here` with:

```
let shader = MPSImageSobel(device: device)
shader.encode(
  commandBuffer: commandBuffer,
  sourceTexture: sourceTexture,
  destinationTexture: drawable.texture)
```

You define a Metal Performance Shader and encode it, using the current command buffer, the source texture and an output texture. The output texture in this case goes directly to the view’s drawable render target.

If you build and run, you’ll get a crash:

failed assertion \`frameBufferOnly texture not supported for compute.&#x27;

<a id="page-715"></a>

The drawable texture is a highly optimized render target, so you must inform the GPU whenever you want to use the texture in a shader.

➤ At the end of `init(metalView:)`, add this code:

`metalView.framebufferOnly = false`

The drawable texture will be less efficient, but you will be able to use it directly in an MPS.

➤ Build and run to see the effect of the Sobel filter:

![Figure](Metal_by_Tutorials_v500mpdf/2d89fc400a705399f586569c.png)

_The Sobel filter_

As you can see, it’s simple to run the shader, and you don’t have to know about how the filter is created.

Note: MPS kernels are not thread-safe, so it’s not recommended to run the same kernel on multiple threads that are all writing to the same command buffer concurrently.

<a id="page-716"></a>

## **Image Processing**

There are a few dozen MPS image filters, among the most common being:

• Morphological (area min, area max, dilate, erode).

• Convolution (median, box, tent, Gaussian blur, Sobel, Laplacian, and so on).

• Histogram (histogram, histogram equalization, histogram specification).

• Threshold (binary, binary inverse, to zero, to zero inverse, and so on).

• Manipulation (conversion, Lanczos scale, bilinear scale, transpose).

Note: For a complete list of MPS kernels, consult Apple’s official Image Filters page (https://developer.apple.com/documentation/metalperformanceshaders/ image\_filters). If you want to create your own filters, you can get inspired from Gimp’s list of filters (https://docs.gimp.org/en/filters.html).

An RGB image is nothing but a matrix with numbers between 0 and 255 (when using 8-bit color channels). A greyscale image only has one such matrix because it only has one channel. For color images, there are three separate RGB channels (red, green, blue), so consequently three matrices, one for each channel.

One of the most important operations in image processing is convolution, which is an operation consisting of applying a much smaller matrix, often called the kernel, to the original image and obtaining the desired effect as a result.

<a id="page-717"></a>

As an example, this matrix is used for obtaining Gaussian blur:

![Figure](Metal_by_Tutorials_v500mpdf/c768a8ccfb46c649270c0e2e.png)

_A Gaussian blur matrix_

Note: You can find a list of common kernels at https://en.wikipedia.org/wiki/ Kernel\_(image\_processing)

Here’s a diagram showing how the kernel is applied to two pixels:

![Figure](Metal_by_Tutorials_v500mpdf/f89116ae882aa83918bc35c8.png)

_Convolution_

And, here’s how the result shown in green was calculated:

```
(6 * 1  +  7 * 2  +  3 * 1  +
 4 * 2  +  9 * 4  +  8 * 2  +
 9 * 1  +  2 * 2  +  3 * 1) / 16 = 6
```

In this example, 16 represents the weight, and it’s not a randomly chosen number — it’s the sum of the numbers from the convolution kernel matrix.

<a id="page-718"></a>

When you need to apply convolution to the border pixels, you can apply padding to the input matrix. For example, when the center of a 3×3 convolution kernel overlaps with the image element at position (0, 0), the image matrix needs to be padded with an extra row and extra column of zeros. However, if the bottom rightmost element of the convolution kernel overlaps with the image element at position (0, 0), the image matrix needs to be padded with two extra rows and two extra columns of zeros.

![Figure](Metal_by_Tutorials_v500mpdf/113aedac882f149945635cb4.png)

_Convolution applied to border pixels_

Applying the convolution kernel to an image matrix padded with an extra row, and extra column of zeros, gives you this calculation for a 3×3 kernel:

```
(0 * 1  +  0 * 2  +  0 * 1  +
 0 * 2  +  6 * 4  +  7 * 2  +
 0 * 1  +  4 * 2  +  9 * 1) / 9 = 6
```

In this case, the weight, 9, is the sum of the numbers from the convolution kernel matrix that are affecting only the non-zero numbers from the image matrix (4 + 2 + 2 + 1). Something like this is straightforward, but when you need to work with larger kernels and multiple images that need convolution, this task might become non-trivial.

You know how to calculate by hand and apply convolution to an image — and at the very beginning of the chapter you saw an MPS filter on an image too — but how about using MPS in your engine?

What if you were to implement **bloom** in your engine?

Guess what? You are going to do just that next!

<a id="page-719"></a>

## **Bloom**

The bloom effect is quite a spectacular one. It amplifies the brightness of objects in the scene and makes them look luminous as if they’re emitting light themselves.

Below is a diagram that gives you an overview of how to achieve bloom:

![Figure](Metal_by_Tutorials_v500mpdf/cfb32d176d6a25d05cd245ef.png)

_The bloom effect_

Here are the steps you’re going to take:

• Render the entire scene to a texture.

• Apply a threshold filter to this texture. This will amplify the lighter parts of the image, making them brighter.

• Apply a blur filter to the threshold texture from the previous step.

• Combine this texture with the initial scene for the final image.

<a id="page-720"></a>

## **The Starter Project**

➤ In Xcode, open the starter project, MPSPostProcessing, and build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/c2dcffcc2fa11ca45cfe8fe2.png)

The scene is the same as Chapter 25, “Managing Resources”, complete with marching skeletons. You can traverse the scene with the WASD keys, and press 2 to reset the view.

The starter project has a new Post Processing folder, already set up with Bloom.swift and Outline.swift. In these files, you’ll add some post processing filters to the final image.

In the Renderer folder, open Renderer.swift, and locate // Post processing in draw(scene:in:). Renderer initializes bloom and outline, and depending on the option that the user chooses, runs a post processing effect.

The project currently renders to the view’s drawable texture. Instead of sending this texture straight to the screen, you’ll intercept and use the drawable texture as input to the threshold filter.

Currently, when you choose Bloom or Outline in the app, a print statement goes to the debug console.

<a id="page-721"></a>

## **Setting Up the Textures**

➤ In the **Post Processing** folder, open **Bloom.swift**, and import the MPS framework:

`import MetalPerformanceShaders`

➤ Define two textures at the top of Bloom:

```
var outputTexture: MTLTexture!
var finalTexture: MTLTexture!
```

outputTexture will hold the blurred threshold texture, and finalTexture will hold this texture combined with the initial render.

Renderer calls resize(view:size:) from mtkView(\_:drawableSizeWillChange:) whenever the window resizes, so this is where you’ll create the textures.

➤ Add the following code to resize(view:size:):

```
outputTexture = TextureController.makeTexture(
  size: size,
  pixelFormat: view.colorPixelFormat,
  label: "Output Texture",
  usage: [.shaderRead, .shaderWrite])
finalTexture = TextureController.makeTexture(
  size: size,
  pixelFormat: view.colorPixelFormat,
  label: "Final Texture",
  usage: [.shaderRead, .shaderWrite])
```

You create the two textures using makeTexture(size:pixelFormat:label:storageMode:usage:) that you first created in Chapter 12, “Render Passes”. TextureController now holds this method. Later, you’ll use these textures as the destinations of MPS filters, so you mark them as writeable.

## **Image Threshold to Zero**

The Metal Performance Shader MPSImageThresholdToZero is a filter that returns either the original value for each pixel having a value greater than a specified brightness threshold or 0. It uses the following test:

```
destinationColor =
  sourceColor > thresholdValue ? sourceColor : 0
```

<a id="page-722"></a>

This filter has the effect of making darker areas black, while the lighter areas retain their original color value.

➤ In postProcess(view:commandBuffer:), replace print(&quot;Post processing: Bloom&quot;) with:

```
guard
  let drawableTexture =
    view.currentDrawable?.texture else { return }
let brightness = MPSImageThresholdToZero(
  device: Renderer.device,
  thresholdValue: 0.3,
  linearGrayColorTransform: nil)
brightness.label = "MPS brightness"
brightness.encode(
  commandBuffer: commandBuffer,
  sourceTexture: drawableTexture,
  destinationTexture: outputTexture)
```

Here, you create an MPS kernel to create a threshold texture with a custom brightness threshold set to 0.3 — where all pixels with less than a color value of 0.3 will be turned to black. The input texture is the view’s drawable texture, which contains the current rendered scene. The result of the filter will go into outputTexture. Internally, the MPS kernel samples from drawableTexture, so you have to set the view’s drawable to be used for read/write operations.

➤ Open Renderer.swift, and add this to the end of init(metalView:options:):

`metalView.framebufferOnly = false`

You need to be able to read and write to the view’s drawable texture. Metal optimizes drawable as much as possible, so setting framebufferOnly to false will affect performance slightly.

To be able to see the result of this filter, you’ll blit outputTexture back into drawable.texture. You should be familiar with the blit command encoder from when you copied textures to the heap in Chapter 25, “Managing Resources”

## **The Blit Command Encoder**

➤ Open Bloom.swift, and add this code to the end of postProcess(view:commandBuffer:):

`finalTexture = outputTexture`

<a id="page-723"></a>

```
guard let blitEncoder = commandBuffer.makeBlitCommandEncoder()
  else { return }
let origin = MTLOrigin(x: 0, y: 0, z: 0)
let size = MTLSize(
  width: drawableTexture.width,
  height: drawableTexture.height,
  depth: 1)
blitEncoder.copy(
  from: finalTexture,
  sourceSlice: 0,
  sourceLevel: 0,
  sourceOrigin: origin,
  sourceSize: size,
  to: drawableTexture,
  destinationSlice: 0,
  destinationLevel: 0,
  destinationOrigin: origin)
blitEncoder.endEncoding()
```

This copies the output of the previous filter into the drawable texture. Unlike when you copied the textures to the heap, you don’t have to worry about slices and mipmap levels here.

➤ Build and run the app, and select Bloom.

You’ll now see the texture filtered to grayscale.

![Figure](Metal_by_Tutorials_v500mpdf/afa65449ab9db2b1faf271a8.png)

_Brightness threshold_

Notice how only some of the rendered areas were bright enough to make it to this texture. These white areas are all you need to create the bloom effect. Before using this texture, you need to add a little fuzziness to it which will make the model edges appear to glow. You can accomplish this with another MPS kernel: the Gaussian blur.

<a id="page-724"></a>

## **Gaussian Blur**

MPSImageGaussianBlur is a filter that convolves an image with a Gaussian blur with a given sigma value (the amount of blur) in both the X and Y directions.

➤ Still in Bloom.swift, in postProcess(view:commandBuffer:), add the following code prior to finalTexture = outputTexture:

```
let blur = MPSImageGaussianBlur(
  device: Renderer.device,
  sigma: 9.0)
blur.label = "MPS blur"
blur.encode(
  commandBuffer: commandBuffer,
  inPlaceTexture: &outputTexture,
  fallbackCopyAllocator: nil)
```

In-place encoding is a special type of encoding where, behind the curtains, the input texture is processed, stored to a temporary texture and finally written back to the input texture without the need for you to designate an output texture.

The fallbackCopyAllocator argument allows you to provide a closure where you can specify what will happen to the input image should the in-place normal encoding fail.

➤ Build and run the app. Choose **Bloom**, and you’ll see the result of this blur.

![Figure](Metal_by_Tutorials_v500mpdf/a875bf551e2fbbcd7d2e215f.png)

_Brightness and blur_

<a id="page-725"></a>

## **Image Add**

The final part of creating the bloom effect is to add the pixels of this blurred image to the pixels of the original render.

MPSImageArithmetic, as its name suggests, performs arithmetic on image pixels. Subclasses of this include MPSImageAdd, MPSImageSubtract, MPSImageMultiply and MPSImageDivide.

Adding the rendered scene pixels to the lighter blurred pixels will brighten up those parts of the scene. In contrast, adding them to the black pixels will leave them unchanged.

➤ In postProcess(view:commandBuffer:), replace finalTexture = outputTexture with this:

```
let add = MPSImageAdd(device: Renderer.device)
add.encode(
  commandBuffer: commandBuffer,
  primaryTexture: drawableTexture,
  secondaryTexture: outputTexture,
  destinationTexture: finalTexture)
```

This code adds the drawable texture to outputTexture and places the result in finalTexture.

➤ Build and run the app, and choose Bloom. You’ll see this:

![Figure](Metal_by_Tutorials_v500mpdf/5a5ad007a7790f52895f6c36.png)

_Brightness, blur and add_

The entire scene is bathed in a mystical glow. Awesome bloom!

<a id="page-726"></a>

➤ In postProcess(view:commandBuffer:), change the initialization of brightness to:

```
let brightness = MPSImageThresholdToZero(
  device: Renderer.device,
  thresholdValue: 0.8,
  linearGrayColorTransform: nil)
```

Fewer pixels will make it through the brightness filter.

➤ Build and run the app, and choose Bloom.

![Figure](Metal_by_Tutorials_v500mpdf/42dd08490fff3412976fdd1a.png)

_Glowing skeletons_

Because the skeletons are the brightest objects in the scene, they appear to glow spookily.

## **Matrix / Vector Mathematics**

You learned in the previous section how you could quickly apply a series of MPS filters that are provided by the framework. But what if you wanted to make your own filters?

You can create your own filter functions and calculate convolutions yourself. However, when working with large matrices and vectors, the amount of math involved might get overwhelming.

The MPS framework not only provides image processing capability, but it also provides functionality for decomposition and factorizing matrices, solving systems of equation and multiplying matrices and/or vectors on the GPU in a fast, highly parallelized fashion. You’re going to look at matrix multiplication next.

<a id="page-727"></a>

➤ In the Utility folder, create a new empty file called Matrix.swift, and add this code to the file:

```
import Playgrounds
import MetalPerformanceShaders

#Playground {
  guard let device = MTLCreateSystemDefaultDevice(),
    let commandQueue = device.makeCommandQueue()
  else { fatalError() }

  let size = 4
  let count = size * size

  guard let commandBuffer = commandQueue.makeCommandBuffer()
    else { fatalError() }

  commandBuffer.commit()
  await commandBuffer.completed()
}
```

With the #Playground macro, you add a playground to your project, where you can experiment with code. This code creates a Metal device, command queue, command buffer and adds a couple of constants you’ll need later. After committing the command buffer, you wait until the GPU operation has completed.

You can see the content of the variables in the Playground Canvas.

![Figure](Metal_by_Tutorials_v500mpdf/5aec25267a0e45d172de995b.png)

_Playground Canvas_

➤ Above the line where you create the command buffer, add a new method that lets you create MPS matrices:

```
func createMPSMatrix(withRepeatingValue: Float) -> MPSMatrix {
  // 1
  let rowBytes = MPSMatrixDescriptor.rowBytes(
```

<a id="page-728"></a>

```
    forColumns: size,
    dataType: .float32)
  // 2
  let array = [Float](
    repeating: withRepeatingValue,
    count: count)
  // 3
  guard let buffer = device.makeBuffer(
    bytes: array,
    length: size * rowBytes,
    options: [])
  else { fatalError() }
  // 4
  let matrixDescriptor = MPSMatrixDescriptor(
    rows: size,
    columns: size,
    rowBytes: rowBytes,
    dataType: .float32)

  return MPSMatrix(buffer: buffer, descriptor: matrixDescriptor)
}
```

Going through the code:

1. Retrieve the optimal number of bytes between one row and the next. Whereas simd matrices expect column-major order, MPSMatrix uses row-major order.

2. Create a new array and populate it with the value provided as an argument to this method.

3. Create a new buffer with the data from this array.

4. Create a matrix descriptor; then create the MPS matrix using this descriptor and return it.

Use this new method to create and populate three matrices. You’ll multiply A and B together, and you’ll place the result in C.

➤ Add the following code just before creating the command buffer:

```
let A = createMPSMatrix(withRepeatingValue: 3)
let B = createMPSMatrix(withRepeatingValue: 2)
let C = createMPSMatrix(withRepeatingValue: 1)
```

➤ Add this code to create a MPS matrix multiplication kernel:

```
let multiplicationKernel = MPSMatrixMultiplication(
  device: device,
  transposeLeft: false,
```

<a id="page-729"></a>

transposeRight: false,   resultRows: size,   resultColumns: size,   interiorColumns: size,   alpha: 1.0,   beta: 0.0)

➤ Below the line where you create the command buffer, add the following code to encode the kernel:

```
multiplicationKernel.encode(
  commandBuffer: commandBuffer,
  leftMatrix: A,
  rightMatrix: B,
  resultMatrix: C)
```

You multiply A and B together, and you place the result in C.

➤ At the end of the #Playground macro, add this code to read C:

```
// 1
let contents = C.data.contents()
let pointer = contents.bindMemory(
  to: Float.self,
  capacity: count)
// 2
(0..<count).forEach {
  let result = pointer.advanced(by: $0).pointee
}
```

<a id="page-730"></a>

Going through the code:

1. Read the result back from the matrix C into a buffer typed to Float, and set a pointer to read through the buffer.

2. Output the values of the buffer to check them.

➤ Refresh the canvas and scroll down to the last command. Choose Value History, and view the contents of the buffer.

![Figure](Metal_by_Tutorials_v500mpdf/eaa94191cd013c72abdb7ad6.png)

_Value history_

You’ll see that the buffer contains 16 values, all of which are the number 24.0. That’s because the matrix is of size 4×4, and multiplying one row of A with one column of B results in the value 24.0, which is 2×3 added four times.

This is only a small matrix, but you can change the size of the matrix in the size variable at the top of the playground macro, and the matrix multiplication will still be blisteringly fast.

<a id="page-731"></a>

## **Challenge**

You may have noticed that in the app where you did the bloom post processing, the Outline option does nothing. Your challenge is to fill out Outline.swift so that you have an outline render:

![Figure](Metal_by_Tutorials_v500mpdf/7ddc9717ddc67e70ead173b8.png)

_Outline_

To achieve this effect, you’ll first use MPSImageSobel(device:), and then feed the output of the sobel filter to MPSImageThresholdBinaryInverse(device:thresholdValue:maximumValue:lin earGrayColorTransform:).

If you have any difficulties, you can review the answer in the challenge folder for this chapter.

## **Key Points**

• Metal Performance Shaders are compute kernels that are performant and easy to use.

• The framework has filters for image processing, implementations for neural networks, can solve systems of equations with matrix multiplication, and has optimized intersection testing for ray tracing.

• Convolution takes a small matrix and applies it to a larger matrix. When applied to an image, you can blur or sharpen or distort the image.

• Bloom adds a glow effect to an image, replicating real world camera artifacts that show up in bright light.

• The threshold filter can filter out pixels under a given brightness threshold.

<a id="page-732"></a>

# 30

# Chapter 30: Proﬁling

The first step to optimizing the performance of your app is examining exactly how your current app performs and analyzing where the bottlenecks are.

Imagine this scenario: You’ve started development on the first level of a new game, Phoenix Island: Rising from the ashes. You’ve created a basic scene, and now you want to find out how well it runs before adding the action.

![Figure](Metal_by_Tutorials_v500mpdf/3a093d5375ec6b679ac11fc5.png)

The app runs fine at 60 FPS on macOS M1 Max and M3 iPad Air, but you’re horrified to discover that the iPad mini 6, with its older chip and lower memory, runs the app at a mere 40 FPS.

In this chapter, you’ll look at some tools to help you analyze performance and find where your bottlenecks are.

<a id="page-733"></a>

Note: Credit for the phoenix model in this app goes to: NORBERTO-3D at Sketchfab (https://is.gd/S6C4FT). All the other models and HDRI sky were created by the folks at Poly Haven (https://polyhaven.com)

## **The Starter App**

➤ In Xcode, review the project for this chapter. There are a number of interesting features.

## **Assets**

First, there are two Assets folders. The one directly under the top level Profiling contains a lot of data, so it points to a folder outside of the Profiling hierarchy. If the content names are red, select both Assets and game-scene.usda, and in the File inspector, click the folder icon. Then, locate and select the assets folder to reconnect the files. The assets folder is the folder that contains both Assets and game-scene.usda.

![Figure](Metal_by_Tutorials_v500mpdf/ee12363b2cc5287c1fa5a161.png)

_Reconnect asset files_

## **The USD Scene**

assets/game-scene.usda is an editable text file that describes the scene. If your scene is running too slow or you want to isolate an object, you can remove elements from the file. For example, to remove the landscape, delete the following lines:

def Mesh &quot;Landscape&quot; (     prepend references ...

<a id="page-734"></a>

```
  )
{
    token visibility = "inherited"
    matrix4d xformOp:transform ...
    uniform token[] xformOpOrder = ["xformOp:transform"]
}
```

USD is a fantastic file format for composing scenes. Unlike the usdz extension, which includes all the textures and meshes for a single object, the usd and usda format points to mesh and texture files in their own separate locations. This means you can split up work on a scene across different parts of your team. All of the def objects in game-scene.usda point to other files in the Assets folder.

The other Assets folder contains single, separately placed objects in usdz and obj formats.

## **The Render Passes**

In **Renderer.swift**, you can see the usual render passes, along with these new ones:

• NatureRenderPass: Nature renders the rocks with one draw call. You’ll see this render pass later in the chapter.

• WaterRenderPass: Water renders the ocean. Unlike the reflection and refraction you learned about in Chapter 22, “Reflection &amp; Refraction”, here, the “reflection” comes from sampling mip map level 5 in the lower half of the skybox texture. There is no refraction, and the depth of the water is calculated using the distance from the centre of the land mass.

• ParticlesRenderPass: Improving on the particles from Chapter 17, “Particle Systems”, particles are now in 3D, rendering the fire in the fire pit.

• UpscalePass: You’ll take a brief look at MetalFX upscaling later.

• Brighten is a post-processing pass that runs the final render target through tone mapping to improve the color.

<a id="page-735"></a>

➤ Build and run the starter app for this chapter.

![Figure](Metal_by_Tutorials_v500mpdf/6f0dbd4e89789143f42bae9c.png)

_The starter app_

This is a top-down aerial view of the island. You can use your WASD and arrow keys to move around and view the scene. Scroll to go up and down on the Y axis. The buttons at the bottom right will take you to different views of the island, where you’ll see the phoenix circling above.

You’re in the early stages of developing Phoenix Island, so the project is not as efficient as it could be, and some of the asset artwork needs upgrading too. As well as the changes you’ll make throughout this chapter, you could upgrade the app to render the scene using GPU-driven indirect encoding commands, and also coalesce some of the render passes.

## Proﬁling

There are a few ways to monitor and tweak your app’s performance. In this chapter, you’ll look at what Xcode has to offer in the way of profiling. You can also use Instruments, which is a powerful app that profiles both CPU and GPU performance. For further information, read Apple’s article Analyzing the performance of your Metal app (https://apple.co/36Qs9FY).

<a id="page-736"></a>

## **Metal Performance HUD**

A great place to start is looking at information about how your app is running is the Metal Performance HUD.

➤ Select the Profiling Scheme at the top of the Xcode window, and choose Edit Scheme.

![Figure](Metal_by_Tutorials_v500mpdf/41f512a1ca5f377667a8a70d.png)

_Edit scheme_

➤ Under Run, choose the Diagnostics tab, and check Show Graphics Overview. This setting engages the HUD.

![Figure](Metal_by_Tutorials_v500mpdf/46ac9d53fb40b45c84cf8a0c.png)

_Diagnostics_

<a id="page-737"></a>

➤ Close the scheme and build and run your app.

![Figure](Metal_by_Tutorials_v500mpdf/cd189d577d4f3b270250273f.png)

_The Metal Performance HUD_

You can immediately see that although the app runs at 60 FPS on the M1 Max and M3 iPad Air, the older chips on iPad mini 6 and M1 iPad Pro struggle to keep up. The app uses about 1.2GB memory, which is almost at the limit for older devices.

## **Culling Back Faces**

You can achieve a quick performance win by not rendering so many vertices. Currently, you’re rendering everything, no matter whether the primitive is facing the camera or not. Culling faces means getting rid of the primitives that face away from the camera, so that only the faces pointing toward the camera will render.

➤ In the Renderer folder, open Renderer.swift, and change let cullFaces = false to:

`let cullFaces = true`

This change will trigger the culling that’s already implemented in your starter app, which applies to all render passes.

<a id="page-738"></a>

➤ Build and run the app, and compare the HUD result.

![Figure](Metal_by_Tutorials_v500mpdf/09551d654f0bed5c03942ff6.png)

_Face culling implemented_

On the iPad mini 6, you can achieve at least a half millisecond performance gain.

You might think that you always want to cull faces, but you do have to be a bit selective. For example, the tower in your scene is a one-sided mesh. If you go to the Tower view in your app and press W to go forward and scroll to go down, your tower will disappear while you’re inside it because you can’t see the back faces.

To find out more about the Metal Performance HUD, watch Apple’s Tech Talk Discover Metal Performance HUD (https://is.gd/1g0r1D).

## **The GPU Report**

➤ With your app running, and in Xcode on the Debug navigator, click FPS.

![Figure](Metal_by_Tutorials_v500mpdf/8d2a3265e4a8281040a1dd84.png)

_The GPU report_

The GPU report shows in the central pane and contains two major GPU metrics.

<a id="page-739"></a>

The first GPU report metric is Frames Per Second, which represents the current frame rate of your app. Your target should always be 60 FPS or better. The screenshot shows an app running on iPad mini 6. There’s a lot of work ahead to get it to run at 60 FPS.

The second GPU report metric is Frame Time. This report represents the actual time spent processing the current frame on the CPU and the GPU. What’s most important here is that the frame does not take longer than 16.6ms which corresponds to 60 FPS.

You know from the Metal Performance HUD that your GPU time is about 20ms, and it’s the GPU time that is pushing the frame time to 25ms. The HUD will be more accurate than the frame time in the Debug navigator.

The general rule is this: If your GPU time is low, but your frame time is high, then you’re CPU-bound. But here, your GPU time is high, so you’re GPU-bound. This means that your command encoding and animation calculations, which happen on the CPU, is of less concern than what’s happening on the GPU.

## **GPU Workload Capture**

In previous chapters, you captured the GPU workload to inspect textures, buffers and render passes. The GPU capture is always the first point of call for debugging. Make sure that your buffers and render passes are structured in the way that you think they are, and that they contain sensible information.

Next, you’ll look at what else GPU capture can show you.

<a id="page-740"></a>

## **Summary**

➤ With your app running, capture the GPU workload, and in the Debug navigator, click Summary.

![Figure](Metal_by_Tutorials_v500mpdf/90743f6433cd5e7bb3e64949.png)

_The summary of your frame_

Note: If the GPU capture fails, check that you have enough free space on your device, and disengage the Metal Performance HUD.

You’ll see an overview of your frame. The Insights section often contains useful insights when you might bind resources on the CPU, but not use them in your shaders. The previous image, under Memory, shows a number of bound unused resources, most noticeably, the Tangent Buffers.

Note: To take full advantage of the GPU capture, you should add a label to all your buffers, so that you can easily track down issues. name Tangent Buffer is a label added in Mesh.swift.

<a id="page-741"></a>

This insight highlights an error in your app. The app should be using the tangent buffer.

➤ In the Shaders folder, open Vertex.metal, and locate the assignment to worldTangent and worldBitangent.

These assignments are currently set to 0, when they should be using the tangent values.

➤ Change the assignments to:

```
.worldTangent = model->normalMatrix * in.tangent,
.worldBitangent = model->normalMatrix * in.bitangent,
```

➤ Build and run the app again.

You’ll notice the scene is much better lit now, with proper specular values.

![Figure](Metal_by_Tutorials_v500mpdf/91747e551651d4d48f24236d.png)

_Tangent buffer enabled_

➤ Capture the GPU workload and check the **Insights** section.

![Figure](Metal_by_Tutorials_v500mpdf/63b3c3f7547b52dd44b320e1.png)

_Bandwidth issues_

<a id="page-742"></a>

Sometimes the GPU capture is not completely reliable. Although the Memory insight still reports a bound unused resource, the Rocks vertex buffer is very much needed by the Nature render pass.

Under the Bandwidth insight, the unused textures are in the Bloom post-processing effect. It’s possible that the MPS encoders are either not as efficient as they could be, or reporting incorrectly.

As to coalescing the encoders, you should review your render passes. The render passes in this app are all separate so that you can understand what’s going on, but they are not efficient. You should set up a render pass system where you can combine some into a single render command encoder.

➤ Click the **API Usage** insight.

![Figure](Metal_by_Tutorials_v500mpdf/1f0b8f7dea372eb9537347f5.png)

_API Usage insights_

There are a lot of redundant bindings. Most of these are the result of not sorting the submeshes by pipeline state at the start of the app. Submeshes use different pipeline states depending on submesh transparency and the model having a skeleton for animation. Sorting by pipeline state will prevent a lot of GPU switching and unnecessary binding.

Checking Insights is a great place to start optimizing your app, as it could pick up a few simple errors.

## **Encoded Command Performance**

The next place to look at profiling your app is in the Debug navigator, which details the performance of render passes and pipeline states.

➤ In the Debug navigator, switch to Group by Pipeline State. You can now see how much relative time each pipeline took during the frame. The total frame time is under Performance.

<a id="page-743"></a>

![Figure](Metal_by_Tutorials_v500mpdf/c9a77b057fb7e8879b817724.png)

_Group by Pipeline State_

Here, you can see that the Forward PSO takes a large percentage of the render time. This is to be expected because you render the USD scene here. However, drilling down into the draws, there’s one draw that takes up a whopping 11% of the render time. You might have found one of the major reasons your app frame rate isn’t buttery smooth.

![Figure](Metal_by_Tutorials_v500mpdf/e0f1bcd9c4bdb944cd835bd9.png)

_Large draw call_

When you select the draw call, you can see that the rendered object is the Landscape.

The speed of the draw largely depends on the bandwidth speed of the buffers and textures. In the case of the Landscape, the vertex buffers aren’t very large, but the base color texture is 21.33MB. Another object that takes 6% of the draw call is the Dutch Ship. This object’s vertex buffer takes up 14MB, which an artist could very likely optimize.

<a id="page-744"></a>

## **Memory**

Inefficient use of memory can do a lot of damage to performance.

➤ In the Debug navigator, click the Memory tool (below Performance) to see how the various resources are allocated in memory:

![Figure](Metal_by_Tutorials_v500mpdf/0ba46534d67a39f66261a6f9.png)

_Resources in memory_

Clicking on the Allocated Size column shows the buffers and textures in order of size. The heap of textures containing the PBR textures for each object is by far the largest resource.

You should be judicious about the size of textures. The color map is the most important, followed by the normal map. When I first exported the scene from Unreal Engine to USD, all the texture maps were the same size, 2048x2048. In app, they all took up 21.33MB of memory each. Reducing the sizes of metallic, roughness and ambient occlusion maps to 1024x1024, they take up 5.33MB each, and to 512x512, only 1.33MB each. This difference allowed the app to run on the iPad mini 6, with no obvious loss of quality.

If you use the asset catalog for your textures, you can more easily set texture variations for different device capabilities. However, this means taking more responsibility for how you store your resources, rather than simply loading a usdz file.

<a id="page-745"></a>

Loss of quality can affect the look of your scene.

![Figure](Metal_by_Tutorials_v500mpdf/5e90dee87f9204ae6d77fb9d.png)

_Landscape texture_

Compare the low quality on the left with the huge 8192x8192 texture on the right. This large texture takes up 341MB in app memory. Instead of shipping with a huge texture, it would be better to tile the underwater part with a small texture, and only put detailed textures where it matters.

You should handle terrain on its own. If you’re going to cover it up with grass, you don’t need a good texture, but if it’s a highlight of your app, you can investigate Apple’s sample Streaming large images with Metal sparse textures (https://is.gd/ wD0aMG).

## **GPU Timeline**

The GPU timeline tool gives you an overview of how your vertex, fragment and compute functions perform, broken down by render pass.

➤ Build and run the app, and capture the GPU workload with a frame count of 3.

![Figure](Metal_by_Tutorials_v500mpdf/fda1e70f3c4174d86757041a.png)

_Capture the GPU workload_

<a id="page-746"></a>

➤ In the Debug navigator, change Group by Pipeline State to Group by API call, and click on Command Buffer.

You’ll see the dependency graph of the frame, with each render pass texture showing how it’s passed on from the previous render pass.

With a few of the render passes removed, this is an overview of the dependency graph:

![Figure](Metal_by_Tutorials_v500mpdf/733a5720580b9da69fc5d7d8.png)

_Render Passes_

This graph highlights the linear nature of your render passes. Each of them, except for the Particle Compute Pass writes to the view’s drawable, resulting in each pass having to wait for the previous pass to finish. For better efficiency, you could parallelize some of the passes by writing to separate render targets, as you did in Chapter 14, “Deferred Rendering”. For example, the Water render pass is quite expensive, so you could do the water calculations in a separate pass, and then combine these into the view’s render target later.

<a id="page-747"></a>

➤ In the Debug navigator, click on Performance.

![Figure](Metal_by_Tutorials_v500mpdf/26fff7f63daf2cbcff9f2aff.png)

_The GPU timeline_

You’ll see a track for each of your vertex, fragment and compute shaders, so you can visualize where in the timeline your shaders are performed, and how long they take to perform. The longest encoders are the Forward Render Pass and the Coalesced 4 Encoders that are the post processing Metal Performance Shaders producing bloom effect. Looks like you’ve found another greedy culprit.

➤ Open **Renderer.swift**, and in `draw(scene:in:)`, comment out:

```
bloom.postProcess(
  view: view,
  commandBuffer: commandBuffer,
  inputTexture: descriptor.colorAttachments[0].texture)
```

<a id="page-748"></a>

➤ Build and run again. Notice how the Metal Performance HUD is now showing that you’re running at 60FPS, with a frame time of 14.5ms (iPad mini 6 statistics).

➤ Capture three GPU frames again, and see the difference in the GPU timeline.

![Figure](Metal_by_Tutorials_v500mpdf/651d6185ac9d9e1b944b41e5.png)

_Without the bloom render pass_

Where you don’t have a dependency, vertex, fragment, and compute shaders can run in parallel. For example, the GPU can perform your Particles compute shader in parallel with the Shadow render pass, whereas the Brighten post-processing effect depends upon the final render target. Unfortunately, when you look at your render passes, each render is dependent on the previous drawable, so there are a few gaps in the timeline.

## **Instancing**

Reducing the number of draw calls is one of the best ways of improving performance. Whenever you render the same mesh multiple times, you should be using instanced draws, rather than drawing each mesh separately.

As an example of an instanced system, the app includes a procedural nature system. Rocks.swift creates a rock pile of 20 rocks with three random shapes, and three random textures.

![Figure](Metal_by_Tutorials_v500mpdf/5c507caa884febfe1340ec6c.png)

_Procedural rocks_

<a id="page-749"></a>

## **The Procedural Nature System**

Using homeomorphic models, you can choose different shapes for each model. Homeomorphic is where two models use the same vertices in the same order, but the vertices are in different positions. A famous example of this is Spot the cow by Keenan Crane.

![Figure](Metal_by_Tutorials_v500mpdf/e9cf5990cc58b8805deb55eb.png)

_Spot by Keenan Crane_

Spot is modeled from a sphere by moving vertices, rather than adding them. Because the vertices are in the same order as the sphere, the uv coordinates don’t change either.

The random shapes of the rocks are modeled in a similar fashion, using the same basic shape, then readjusting the vertices for each shape. Each adjusted shape is called a morph target.

![Figure](Metal_by_Tutorials_v500mpdf/43aea7aef301fa91f9470a16.png)

_Homeomorphic rocks_

For the rocks, Nature loads the three vertex meshes into one buffer, and each rock, when initialized, is allocated a random number between 0 and 2. It’s then simple to extract the correct mesh from the buffer in the vertex function.

<a id="page-750"></a>

The most important feature of the nature system is that, depending on how powerful your device is, it can render numerous instances with one draw call:

```
 encoder.drawIndexedPrimitives(
   type: .triangle,
   indexCount: submesh.indexCount,
   indexType: submesh.indexType,
   indexBuffer: submesh.indexBuffer.buffer,
   indexBufferOffset: submesh.indexBuffer.offset,
   instanceCount: instanceCount)
```

In Nature.metal, vertex\_nature uses the instance\_id attribute to extract the transform information for the current instance. With the morph target, the vertex function renders a random shape. With the texture ID, the fragment function renders a random texture.

The files involved in the nature system are:

• Common.h: Contains a NatureInstance structure which holds a random texture and shape ID as well as the model and normal matrix.

• Nature.swift: This is in the Geometry folder and is a cut-down version of Model. It loads up the mesh and creates a buffer that contains an array of NatureInstance, one element for each instance.

• Nature.metal: Contains the vertex and fragment functions.

• NatureRenderPass.swift: Renders the scene’s nature array, in the same way as ForwardRenderPass.

➤ Examine these files to see how the nature system works.

## **Inspecting Shaders**

It’s easy to debug Swift code by using break points and printing out values. But how do you find out what your Metal Shading Language code is doing? The Shader editor has you covered. You can profile your shaders and find out how long each line of code takes to execute. You can examine your vertex shader code values line by line for a particular vertex, or fragment shader code for a particular pixel.

Maybe you want to change the color of the ocean, but re-running and returning to the same app state every time is a pain. Or perhaps you want to understand how the foam on the wave works.

<a id="page-751"></a>

➤ Build and run your app. Go to the Tower view, and rotate it until you have a better view of the ocean.

![Figure](Metal_by_Tutorials_v500mpdf/baf54b9a96100057586e1611.png)

_An ocean view_

➤ Capture one frame of the GPU workload and click the Command Buffer. Locate the Water Render Pass, and double-click the render target until you see the full texture.

![Figure](Metal_by_Tutorials_v500mpdf/ad6ba28a926c96dbf907d8dd.png)

_The Water Render Pass_

➤ Click the Debug Shader icon, which looks like a bug, in the toolbar above the Debug console.

![Figure](Metal_by_Tutorials_v500mpdf/9545984ce342f9946f1901d9.png)

_The Debug Shader icon_

<a id="page-752"></a>

Here, you can can either debug the geometry in the vertex or pixels in the fragment shader.

![Figure](Metal_by_Tutorials_v500mpdf/8966b33ff90c48d5ab5e0db7.png)

_Choose vertex or fragment_

➤ Click on a pixel that you want to examine, and choose Fragment Shader and click the bug icon in the right corner of the window.

The fragment function will then run for the selected pixel and the code with calculated values will show.

![Figure](Metal_by_Tutorials_v500mpdf/78a21d7896be4d4525c23215.png)

_Shader function values_

The Debug navigator lists each function command. If you call other functions, you can click the disclosure triangle to navigate to the code there.

On the right, you’ll see each calculated value.

➤ Change `float3 nearColor = farColor * 0.1;` to:

`float3 nearColor = float3(1, 0, 0);`

<a id="page-753"></a>

➤ Click the Reload Shaders arrow in the toolbar above the Debug console.

![Figure](Metal_by_Tutorials_v500mpdf/c6d513a791a6d6e2708cc262.png)

_The Reload Shaders icon_

You should have your render target side by side with your shader code, and you’ll see the result of the shader being re-run.

![Figure](Metal_by_Tutorials_v500mpdf/3cbf7898d01a7646d814b231.png)

_A red sea_

Wait for Xcode to finish profiling the code after you change it. When it’s done, you can experiment with how each command affects the render target. You can return values early, such as checking out the fresnel value.

When you’ve finished making your changes to the shader, make sure you copy the code. When you stop the GPU frame capture, Xcode should ask you whether you want to save changes, but often, it doesn’t.

➤ Click the blue Shader Debugger bug icon to exit the Shader Debugger.

## The Shader Proﬁler

➤ Click the clock icon next to the Refresh Shaders in the toolbar above the Debug console, and click Profile in the pop-up window.

Xcode will now time each operation of your shader code.

![Figure](Metal_by_Tutorials_v500mpdf/bc43c9d9ec352a56a4d247e6.png)

_The Shader Profiler_

<a id="page-754"></a>

You can run your cursor over the circles to see a breakdown of operations. Analyze the percentages for each GPU activity. A high number might indicate an opportunity for performance optimization.

Here’s an opportunity for optimization using shader profiling. Processing floats takes more time than processing other types. As you might know, a half is, well, half the size of a float, so you can optimize this one spot.

➤ With the profiler still running, check the percentage for the value returned from fragment\_water. This will vary slightly each time you profile. On my M1 Max MacBook Pro, it’s 5.69%.

➤ Change the fragment header so that you return a half4 instead of a float4 and change the return value to:

`return half4(half3(color), alpha);`

➤ Click Reload Shaders and wait for the profiling to finish.

The percentage on my computer lowered to 4.63%. The cost of processing halfs over floats is less, and it’s an easy change to make to your shader functions. Do ensure that you don’t need the extra precision of the float value though. Other ALU optimizations you can do include replacing ints with shorts, simplifying complex instructions such as trigonometry functions (sin, cos, etc.) and other arithmetic calculations.

## **CPU-GPU Synchronization**

Measuring GPU performance is important, but you should also consider interaction between CPU and GPU. Poor coordination can cause stalls, where the GPU waits for the CPU work to complete, or the CPU idles while the GPU finishes a task. Synchronization issues can also cause frame stutters.

Managing dynamic data can be a little tricky. Take the case of Uniforms, which is now stored in an MTLBuffer, rather than a simple structure, to help you understand synchronization. Uniforms contains only camera and shadow data, so you update it usually once per frame on the CPU. That means that the GPU should wait until the CPU has finished writing the buffer before it can read the buffer.

Instead of halting the GPU’s processing, you can have a pool of reusable buffers.

<a id="page-755"></a>

## **Triple Buffering**

Triple buffering is a well-known technique in the realm of synchronization. The idea is to use three buffers at a time. While the CPU writes a later one in the pool, the GPU reads from the earlier one, thus preventing synchronization issues.

![Figure](Metal_by_Tutorials_v500mpdf/e8559563e659af5a56bdc200.png)

You might ask, why three and not just two or a dozen? With only two buffers, there’s a high risk that the CPU will try to write the first buffer again before the GPU finished reading it even once. With too many buffers, there’s a high risk of performance issues.

➤ In the Renderer folder, open Renderer.swift.

At the top of the file, you’ll see a global variable which determines the number of frames in flight. Frames in flight is a graphics term for how many frames you can write to at once. Renderer.currentFrameIndex keeps track of the current frame.

➤ Change `let maxFramesInFlight = 1` to:

`let maxFramesInFlight = 3`

When the app creates the initial uniforms buffer array, it will now create an array of three of them.

➤ Locate Renderer.updateUniforms(scene:) and examine the code. In previous chapters you were updating Uniforms, a structure. Now you update the contents of the Metal buffer for the current frame.

<a id="page-756"></a>

➤ At the start of draw(scene:in:), after guard, add this code to update the current frame:

```
Self.currentFrameIndex =
  (Self.currentFrameIndex + 1) % maxFramesInFlight
```

Here, you make the index loop around always taking the values 0, 1 and 2.

➤ Build and run the app.

![Figure](Metal_by_Tutorials_v500mpdf/15317df65b2c8047d1a374df.png)

_Result of triple buffering_

Your app shows the same scene as before. However, in this example you probably won’t notice any difference.

There is some bad news. The CPU can write to uniforms at any time and the GPU can read from it. There’s no synchronization to ensure the correct uniform buffer is being read. When there is little action going on in your app, that’s not so important, but when you want to keep track of all sorts of camera and animation information, you need to ensure that the GPU is getting correct and timely data.

The problem is known as resource contention and involves conflicts, known as race conditions, over accessing shared resources by both the CPU and GPU. This can cause unexpected results, such as animation glitches.

In the image below, the CPU is ready to start writing the first buffer again. However, that would require the GPU to have finished reading it, which is not the case here.

<a id="page-757"></a>

The following example shows two uniform buffers available:

![Figure](Metal_by_Tutorials_v500mpdf/6e826fa17413802c49e3650e.png)

_Resource Contention_

What you need here is a way to delay the CPU writing until the GPU has finished reading it.

![Figure](Metal_by_Tutorials_v500mpdf/c731af23a157b25572b86cae.png)

A naive approach is to block the CPU until the command buffer has finished executing.

➤ Still in Renderer.swift, add this to the end of draw(scene:in:):

`commandBuffer.waitUntilCompleted()`

➤ Build and run the app.

You’re now sure that the CPU thread is successfully being blocked, so the CPU and GPU are not fighting over uniforms. However, causing the CPU to wait until the GPU has finished may affect the frame rate.

<a id="page-758"></a>

## **Semaphores**

A more performant way, is the use of a synchronization primitive known as a semaphore, which is a convenient way of keeping count of the available resources. In this case, your triple buffer.

Here’s how a semaphore works:

• Initialize it to a maximum value that represents the number of resources in your pool (3 buffers here).

• Inside the draw call the thread tells the CPU to wait until a resource is available and if one is, it takes it and decrements the semaphore value by one.

• If there are no more available resources, the current thread is blocked until the semaphore has at least one resource available.

• When a thread finishes using the resource, it’ll signal the semaphore by increasing its value and by releasing the hold on the resource.

Time to put this theory into practice.

➤ At the top of `Renderer`, add this new property:

`var semaphore: DispatchSemaphore`

➤ In init(metalView:options:), add this before super.init():

`semaphore = DispatchSemaphore(value: maxFramesInFlight)`

➤ Add this code to draw(scene:in:), before updateUniforms(scene:):

`_ = semaphore.wait(timeout: .distantFuture)`

Note: If you add the semaphore wait before if doUpscaling, then, if there is a return from that conditional, the scene will never render. The CPU will be forever waiting for the semaphore to signal completion.

➤ At the end of draw(scene:in:), but before committing the command buffer, add this:

```
commandBuffer.addCompletedHandler { _ in
  self.semaphore.signal()
```

<a id="page-759"></a>

`}`

➤ At the end of `draw(scene:in:)`, remove:

`commandBuffer.waitUntilCompleted()`

➤ Build and run the app again, making sure everything still renders as it did before.

Your frame rate may have reduced slightly. But now the frame renders more accurately without fighting over resources.

## **MetalFX Upscaling**

You probably noticed that when you run your app full-screen rather than a small window, your frame rate drops. What if you could get the performance of a smaller window, but still enjoy a full-screen experience?

That’s what MetalFX gives you. There are two ways to upscale your renders:

• Spatial upscaling enlarges a render texture using advanced graphics techniques.

• Temporal antialiased upscaling takes samples from previous frames and integrates them with the current frame render.

➤ In the Render Passes folder, open UpscalePass.swift.

This pass is ready for you to use, showing how simple the technique is to implement. You create an render texture at a small size, and a final texture for the upscaled result. You also update a render pass descriptor each frame with the current textures, then encode the textures with the MTLFXSpatialScalar.

Renderer updates the view’s drawableSize to match the down-scaled render texture.

➤ First, build and run with the Metal Performance HUD engaged. Take a note of the GPU time, and also the quality of the render.

➤ Open Renderer.swift, and at the top of the file, change let doUpscaling = false to:

`let doUpscaling = true`

Changing this flag will cause Renderer to reduce the view’s drawable size by kUpscaleAmount, currently set to 1.25.

<a id="page-760"></a>

➤ Build and run the app again, and compare the difference. With an upscaling of 1.25, the frame rate improves very slightly, and the quality is still acceptable. An upscaling of 2 gives a great frame rate, but makes the render very muddy.

![Figure](Metal_by_Tutorials_v500mpdf/174b917a08ebdcec57b1bb95.png)

_Result of upscaling_

As always, check what is acceptable to you and your current renders. In some situations, upscaling may even make your frame times slower due to the encoding overhead.

## **Visibility Culling**

The fastest geometry to render is geometry that you don’t have to render because it’s not in the frame. Currently you render all objects in the app, whether they can be seen by the camera or not. You process the fire particles even though they might not be on screen. Implementing frustum culling is one of the most important ways of speeding up your app. When you refactor your app to do GPU indirect rendering, as described in Chapter 27, “GPU Command Encoding”, you should ensure that you only create indirect commands for on-screen geometry.

<a id="page-761"></a>

## **Key Points**

• The Metal Performance HUD is the easiest way to profile your app.

• Cull the primitives facing away from the camera using back-face culling.

• Capture the GPU workload for insight into what’s happening on the GPU. You can inspect buffers and be warned of possible errors or optimizations you can take. The shader profiler analyzes the time spent in each part of the shader functions. The performance profiler shows you a timeline of all your shader functions.

• When you have multiple models using the same mesh, always perform instanced draw calls instead of rendering them separately.

• Textures can have a huge effect on performance. Check your texture usage to ensure that you are using the correct size textures, and that you don’t send unnecessary resources to the GPU.

## **Where to Go From Here?**

The resources for this chapter contain a list of the Apple articles and videos on profiling. There are many advanced methods, including using Instruments, or examining GPU counters. The Apple documentation and videos are very good on this topic. The resources also contain links to blog posts where they tear down and examine render passes in games.

<a id="page-762"></a>

# 31

# Chapter 31: Best Practices

When you want to squeeze the very last ounce of performance from your app, you should always remember to follow a golden set of best practices. These rules are categorized into three major parts: general performance, memory bandwidth and memory footprint. This chapter will guide you through all three.

<a id="page-763"></a>

## **General Performance Best Practices**

The next five best practices are general and apply to the entire pipeline.

## **Choose the Right Resolution**

The game or app UI should be at native or close to native resolution so the UI will always look crisp no matter the display size. Also, it is recommended (albeit not mandatory) that all resources have the same resolution. You can check the resolutions in the GPU Debugger on the dependency graph. Below is a partial view of the dependency graph from the multi-pass render in Chapter 14, “Deferred Rendering”:

![Figure](Metal_by_Tutorials_v500mpdf/50e2bb4afa8de91ed6ad03e4.png)

_The dependency graph_

Notice the size of the shadow pass render target. For crisper shadows, you should have a large texture, but you should consider the performance trade-offs of each image resolution and carefully choose the scenario that best fits your app needs.

## **Optimize Shader Pipelines**

Group draw calls by shader to minimize changing your pipeline states. Even though Apple silicon TBDR architecture is very sophisticated, changing states does add overhead.

When creating your shaders, use function specialization like you did for the skeleton in Chapter 24, “Character Animation”. The fragment shaders currently have conditionals in them where a texture may be missing. This is an opportunity for improvement by changing to function specialization and removing the conditionals.

<a id="page-764"></a>

## **Submit GPU Work Early**

You can reduce latency and improve the responsiveness of your renderer by making sure all of the off-screen GPU work is done early and is not waiting for the on-screen part to start. You can do that by using two or more command buffers per frame:

create off-screen command buffer encode work for the GPU commit off-screen command buffer ... get the drawable create on-screen command buffer encode work for the GPU present the drawable commit on-screen command buffer

Create the off-screen command buffer(s) and commit the work to the GPU as early as possible. Get the drawable as late as possible in the frame, and then have a final command buffer that only contains the on-screen work.

## Stream Resources Efﬁciently

All resources should be allocated at launch time — if they’re available — because that will take time and prevent render stalls later. If you need to allocate resources at runtime because the renderer streams them, you should make sure you do that from a dedicated thread.

You can see resource allocations in Instruments, in a Metal System Trace, under the GPU ➤ Allocation track:

![Figure](Metal_by_Tutorials_v500mpdf/190e636b13385f0798df3c19.png)

You can see here that there are a few allocations, but all at launch time. If there were allocations at runtime, you would notice them later on that track and identify potential stalls because of them.

<a id="page-765"></a>

## **Design for Sustained Performance**

You should test your renderer under a serious thermal state. This can improve the overall thermals of the device, as well as the stability and responsiveness of your renderer.

Xcode now lets you see and change the thermal state in the Devices window from Window ▸ Devices and Simulators.

![Figure](Metal_by_Tutorials_v500mpdf/b765445b89a68ffd525ea5fe.png)

You can also use Xcode’s Energy Impact gauge to verify the thermal state that the device is running at:

![Figure](Metal_by_Tutorials_v500mpdf/072d3ee4332a3af5cfac15d2.png)

<a id="page-766"></a>

## **Memory Bandwidth Best Practices**

Since memory transfers for render targets and textures are costly, the next five best practices are targeted to memory bandwidth and how to use shared and tiled memory more efficiently.

## **Compress Texture Assets**

Compressing textures is very important because sampling large textures may be inefficient. For that reason, you should generate mipmaps for textures that can be minified. You should also compress large textures to accommodate the memory bandwidth needs. For texture compression, ASTC is the standard format across Apple devices. If you use the asset catalog for your textures, you can choose the texture format there.

With the frame captured, you can use the Metal Memory Viewer to verify compression format, mipmap status and size. You can change which columns are displayed by right-clicking the column heading:

![Figure](Metal_by_Tutorials_v500mpdf/9ea14ed62ede048b1c6f4978.png)

_The Metal Memory Viewer_

## **Optimize for Faster GPU Access**

You should configure your textures correctly to use the appropriate storage mode depending on the use case. Use the private storage mode so only the GPU has access to the texture data, allowing optimization of the contents:

```
textureDescriptor.storageMode = .private
textureDescriptor.usage = [ .shaderRead, .renderTarget ]
let texture = device.makeTexture(descriptor: textureDescriptor)
```

<a id="page-767"></a>

Use shared storage mode for textures only when the CPU needs to access them as well as the GPU.

You shouldn’t set any unnecessary usage flags. Only use shaderWrite when you actually need to write to the texture, such as during a compute shader.

Shared textures that can be accessed by the CPU as well as the GPU should explicitly be optimized after any CPU update on their data:

```
textureDescriptor.storageMode = .shared
textureDescriptor.usage = .shaderRead
let texture = device.makeTexture(descriptor: textureDescriptor)
// update texture data
texture.replace(
  region: region,
  mipmapLevel: 0,
  withBytes: bytes,
  bytesPerRow: bytesPerRow)
let blitCommandEncoder = commandBuffer.makeBlitCommandEncoder()
blitCommandEncoder
  .optimizeContentsForGPUAccess(texture: texture)
blitCommandEncoder.endEncoding()
```

Again, the Metal Memory Viewer shows you the storage mode and usage flag for all textures, along with noticing which ones are compressed textures already, as in the previous image.

## **Choose the Right Pixel Format**

Choosing the correct pixel format is crucial. Not only will larger pixel formats use more bandwidth, but the sampling rate also depends on the pixel format. You should try to avoid using pixel formats with unnecessary channels and also try to lower precision whenever possible. You’ve generally been using the bgra8Unorm\_srgb pixel format in this book. However, when you needed greater accuracy for the G- Buffer in Chapter 14, “Deferred Rendering”, you used a 16-bit pixel format. Again, you can use the Metal Memory Viewer to see the pixel formats for textures.

## **Optimize Load and Store Actions**

Load and store actions for render targets can also affect bandwidth. If you have a suboptimal configuration of your pipelines caused by unnecessary load/store actions, you might create false dependencies. An example of optimized configuration would be as follows:

`renderPassDescriptor.colorAttachments[0].loadAction = .clear`

<a id="page-768"></a>

`renderPassDescriptor.colorAttachments[0].storeAction = .dontCare`

In this case, you’re configuring a color attachment to be transient, which means you do not want to load or store anything from it. You can verify the current actions set on render targets in the Dependency Viewer.

You can see here the GPU wrongly stores the depth texture, even though it isn’t passed to a following render pass.

![Figure](Metal_by_Tutorials_v500mpdf/488f7c24209d2b0831f8a406.png)

_Redundant store action_

## **Optimize Multi-Sampled Textures**

Apple’s TBDR architecture handles MSAA efficiently in tile memory. When implementing MSAA, make sure not to load or store the MSAA texture and set its storage mode to memoryless:

```
textureDescriptor.textureType = .type2DMultisample
textureDescriptor.sampleCount = 4
textureDescriptor.storageMode = .memoryless
let msaaTexture = device.makeTexture(descriptor:
textureDescriptor)
renderPassDesc.colorAttachments[0].texture = msaaTexture
renderPassDesc.colorAttachments[0].loadAction = .clear
renderPassDesc.colorAttachments[0].storeAction
= .multisampleResolve
```

<a id="page-769"></a>

MSAA still increases GPU workload, so first evaluate whether the visual improvement is worth it.

## **Memory Footprint Best Practices**

## **Use Memoryless Render Targets**

As mentioned previously, you should be using memoryless storage mode for all transient render targets that do not need a memory allocation, that is, are not loaded from or stored to memory:

```
textureDescriptor.storageMode = .memoryless
textureDescriptor.usage = [.shaderRead, .renderTarget]
// for each G-Buffer texture
textureDescriptor.pixelFormat = gBufferPixelFormats[i]
gBufferTextures[i] =
  device.makeTexture(descriptor: textureDescriptor)
renderPassDescriptor.colorAttachments[i].texture =
  gBufferTextures[i]
renderPassDescriptor.colorAttachments[i].loadAction = .clear
renderPassDescriptor.colorAttachments[i].storeAction = .dontCare
```

You’ll be able to see the change immediately in the dependency graph.

## **Avoid Loading Unused Assets**

Loading all the assets into memory will increase the memory footprint, so consider the memory and performance trade-off, and only load all the assets that you know will be used. The GPU frame capture Memory Viewer will show you any unused resources.

## **Use Smaller Assets**

You should only make the assets as large as necessary and consider the image quality and memory trade-off of your asset sizes. Make sure that both textures and meshes are compressed. You may want to only load the smaller mipmap levels of your textures or use lower level of detail meshes for distant objects.

<a id="page-770"></a>

## **Simplify memory-intensive effects**

Some effects may require large off-screen buffers, such as Shadow Maps and Screen Space Ambient Occlusion, so you should consider the image quality and memory trade-off of all of those effects, potentially lower the resolution of all these large off-screen buffers and even disable the memory-intensive effects altogether when you are memory constrained.

## **Use Metal Resource Heaps**

Rendering a frame may require a lot of intermediate memory, especially if your game becomes more complex in the post-process pipeline, so consider using Metal Resource Heaps for those effects and alias as much of that memory as possible. For example, you may want to reutilize the memory for resources that have no dependencies, such as those for Depth of Field or Screen-Space Ambient Occlusion.

Another advanced concept is that of purgeable memory. Purgeable memory has three states: non-volatile (when data should not be discarded), volatile (data can be discarded even when the resource may be needed) and empty (data has been discarded). Volatile and empty allocations do not count towards the application’s memory footprint because the system can either reclaim that memory at some point or has already reclaimed it in the past.

## **Mark Resources as Volatile**

Temporary resources may become a large part of the memory footprint and Metal will allow you to set the purgeable state of all the resources explicitly. You will want to focus on your caches that hold mostly idle memory and carefully manage their purgeable state, like in this example:

```
// for each texture in the cache
texturePool[i].setPurgeableState(.volatile)
// later on...
if (texturePool[i].setPurgeableState(.nonVolatile) == .empty) {
  // regenerate texture
}
```

<a id="page-771"></a>

## **Manage the Metal PSOs**

Pipeline State Objects (PSOs) encapsulate most of the Metal render state. You create them using a descriptor that contains vertex and fragment functions as well as other state descriptors. All of these will get compiled into the final Metal PSO.

Metal allows your application to load most of the rendering state upfront. However, if you have limited memory, make sure not to hold on to PSO references that you don’t need anymore. Also, don’t hold on to Metal function references after you have created the PSO cache because they are not needed to render; they are only needed to create new PSOs.

Note: Apple has written a Metal Best Practices guide (https:// developer.apple.com/library/archive/documentation/3DDrawing/Conceptual/ MTLBestPracticesGuide/index.html) that provides great advice for optimizing your app.

## **Where to Go From Here?**

Getting the last ounce of performance out of your app is paramount. You’ve had a taste of examining CPU and GPU performance using Xcode, but to go further, you’ll need to use Instruments with Apple’s Instruments documentation (https:// help.apple.com/instruments/mac/10.0/).

Over the years, at every WWDC since Metal was introduced, Apple has produced some excellent WWDC videos describing Metal best practices and optimization techniques. Go to https://developer.apple.com/videos/graphics-and-games/metal/ and watch as many as you can, as often as you can.

Congratulations on completing the book! The world of Computer Graphics is vast and as complex as you want to make it. But now that you know the basics of Metal, even though current internet resources are few, you should be able to learn techniques described with other APIs, such as OpenGL, Vulkan and DirectX. If you’re keen to learn more, check out the great books in the resources folder for this chapter.

<a id="page-772"></a>

# 32

# Conclusion

Thank you again for purchasing Metal by Tutorials. If you have any questions or comments as you continue to develop for Metal, please stop by our forums at https:// forums.kodeco.com.

Your continued support is what makes the tutorials, books, videos and other things we do at Kodeco possible. We truly appreciate it.

Best of luck in all your development and game-making adventures,

– Caroline Begbie (Author), Marius Horga (Author), Adrian Strahan (Tech Editor) and Tammy Coron (FPE).

The _Metal by Tutorials_ team
