.. blogpost::
   :title: HRCS Stereo Segmentation Final Report
   :author: atrevor
   :date: 11-13-2012

   The Honda Research Code Sprint for ground segmentation from stereo has been completed.  PCL now includes tools for generating disparity images and point clouds from stereo data courtesy of Federico Tombari, as well as tools for segmenting a ground surface from such point clouds from myself.  Attached is a report detailing the additions to PCL and the results, as well as a video overview of the project.  There is a demo available in trunk apps, as pcl_stereo_ground_segmentation.

   .. raw:: html

      <center><iframe width="420" height="315" src="http://www.youtube.com/embed/F6VilFDbaSQ" frameborder="0" allowfullscreen></iframe></center>

      <center><iframe src="http://docs.google.com/viewer?url=http://svn.pointclouds.org/hrcsweb/source/atrevor/files/hrcs_report.pdf&amp;embedded=true" style="border: none;" height="400" width="800"></iframe></center>

.. blogpost::
   :title: Pointclouds from outdoor stereo cameras
   :author: atrevor
   :date: 6-4-2012

   I recently recieved stereo data and disparity maps to work with for this project, so I wrote a tool to convert the disparity maps to PCD files.  The provided disparity data has been smoothed somewhat, which I think might be problematic for our application.  For this reason, I also produced disparities usign OpenCV's semi-global block matching algorithm, which produces quite different results.  You can see an example here:

   .. image:: img/rect_imgL06212.png
      :align: center

   Above is the left image of the input scene.  Note the car in the foreground, the curb, and the more distant car on the left of the image.

   .. image:: img/sgbm_top_down.png
      :align: center

   Above is a top-down view of a point cloud generated by OpenCV's semi-global block matching.  The cars and curb are visible, though there is quite a bit of noise.

   .. image:: img/smoothed_top_down.png
      :align: center

   Above is an image using the provided disparities, which included some smoothing.  The curb is no longer visible, and there is also an odd "ridge" in the groudnplane starting at the front of the car.  I think this will be problematic for groundplane segmentation.  Both approaches seem to have some advantages and disadvantages, so I'll keep both sets of PCDs around for testing.  Now that I have PCD files to work with, I'm looking forward to using these with my segmentation approach.  Prior to using stereo data, I developed segmentation for use on Kinect.  I think the main challenge in applying this approach to stereo data will be dealing with the reduced point density and greatly increased noise.  I'll post more on this next time.
